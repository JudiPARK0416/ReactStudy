# 🔠 How I Fixed the "Filename Case Mismatch" Error in Git & VSCode

`#React` `#Git` `#VSCode` `#Filename-Casing` `#TIL` `#Today-I-Learned`  
**Judy Park, 10 April 2025**

While working on a simple React project, I ran into a frustrating error related to file name casing. The file was definitely there, but VSCode and TypeScript just wouldn’t let me import it. Here's how I solved it — and why it happened in the first place.

---

## 🧠 The Error

I had a component named `Profile.jsx` and tried to import it like this:

```jsx
import Profile from "./components/Profile.jsx";
```

But VSCode gave me this error:

```bash
Already included file name '.../Profile.jsx' differs from '.../profile.jsx' only in casing.
```

> "Wait... is that even a problem?"

Yes. Because of how different systems treat **filename casing**, this can be a real issue — especially when using Git.

---

## ⚙️ Why This Happens

| System/Tool      | Case-sensitive?                                           |
| ---------------- | --------------------------------------------------------- |
| macOS / Windows  | ❌ No (treat `Profile.jsx` and `profile.jsx` as the same) |
| Git / TypeScript | ✅ Yes (treat them as completely different files)         |

If at any point a file was named `profile.jsx` and later renamed to `Profile.jsx`, Git may **not detect** that change — especially on macOS. That’s where the conflict starts.

---

## ✅ The Fix

### 1. Force Git to Recognize the Case Change

Rename the file temporarily and then rename it back to the desired casing:

```bash
git mv src/components/Profile.jsx src/components/temp.jsx
git mv src/components/temp.jsx src/components/Profile.jsx
git commit -am "Fix filename casing for Profile.jsx"
```

> This forces Git to treat the rename as a real change.

---

### 2. Restart VSCode or TypeScript Server

Even after fixing the filename, VSCode may still complain. That’s because it **caches file paths**.

#### Solutions:

- Restart VSCode completely  
  **OR**
- Use the Command Palette:  
  `Cmd + Shift + P` → `TypeScript: Restart TS Server`

---

### 3. Check Your Import Statement

Make sure your import path exactly matches the filename:

✅ Correct:

```js
import Profile from "./components/Profile";
```

🚫 Incorrect (wrong case):

```js
import Profile from "./components/profile";
```

You can also omit the `.jsx` extension, as tools like Vite automatically resolve it.

---

## 🩺 Real-life Analogy: Emergency Gear

Imagine trying to find an “AED” in an emergency, but someone labeled it “aed.”  
Humans might not care, but a computer system might completely miss it.  
That's exactly what’s happening here: your system doesn't care, but Git does.

---

## 🧾 Final Checklist

- [x] Renamed file using `git mv` to reflect case changes
- [x] Updated import paths to match exact casing
- [x] Restarted VSCode or TypeScript server
- [x] Successfully committed and pushed the fix

---

Hope this helps you avoid the same confusion I had!  
If you’re using macOS or Windows, always double-check **filename casing** when weird import issues pop up.

Happy coding! 🚀