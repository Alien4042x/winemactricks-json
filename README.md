# 🍷 WineMacTricks JSON Database

Custom tweak database for macOS Wine-based wrappers (CrossOver, CXPatcher).  
These tweaks are consumed by the [BottleForge](https://github.com/Alien4042x/BottleForge) app.

---

## 🛠️ Example Tweaks

### 1. Simple DLL Override

```json
{
  "id": "example.mscoree_fix",
  "title": "Example App – mscoree.dll Fix",
  "description": "Fix black screen during loading.",
  "description_long": "Fixes a freeze or black screen that occurs while loading the app. This issue is caused by a missing .NET component. Setting mscoree.dll to native resolves the problem.",
  "category": "dll",
  "applies_to": ["ExampleApp.exe"],
  "company": "ExampleSoft",
  "platforms": ["Steam"],
  "steps": ["Set native override"],
  "files": [
    {
      "dll": "mscoree",
      "mode": "native"
    }
  ]
}
```

---

### 2. Advanced Tweak (File + Registry)

```json
{
  "id": "example.libcef_fix",
  "title": "Example App – libcef.dll Fix",
  "description": "Fix crash at startup by adding libcef.dll and setting native override.",
  "description_long": "This tweak fixes the startup crash by copying libcef.dll and setting it as native override in Wine registry.",
  "category": "dll",
  "applies_to": ["ExampleApp.exe"],
  "company": "ExampleSoft",
  "platforms": ["Steam"],
  "steps": [
    "Download libcef.dll",
    "Place into system32",
    "Set native override"
  ],
  "files": [
    {
      "name": "libcef.dll",
      "source_url": "https://cdn.example.com/libcef.dll",
      "destination": "system32/libcef.dll"
    }
  ],
  "actions": [
    {
      "type": "copy_dll",
      "source_url": "https://cdn.example.com/libcef.dll",
      "destination": "system32/libcef.dll"
    },
    {
      "type": "reg_override",
      "dll": "libcef",
      "mode": "native"
    }
  ]
}
```

---

## ⚠️ Notes

- Each tweak inside the `"tweaks"` array **must be separated by a comma**.
- The `actions` array is optional, but allows for more advanced logic.
- Categories can include:
  - `dll`, `registry`, `config`, `audio`, `misc`...
- Ensure valid JSON format: no trailing commas, correct escaping.

---

## 📦 Used in

- [BottleForge.app](https://github.com/Alien4042x/BottleForge)

---

## ✨ License

MIT or Public Domain — use freely.
