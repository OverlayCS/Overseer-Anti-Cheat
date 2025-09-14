# Overseer Anti-Cheat

Overseer is a lightweight, Unity-friendly anti-cheat framework designed for VR games.  
It focuses on **stopping sideloaded / repacked APKs**, **detecting DLL (native library) injection**, and **blocking unauthorized modifications** — aiming to prevent 99.99% of common modding attempts.

---

## ✨ Features

- **APK Verification**  
  Detects repacked, tampered, or sideloaded builds before they can run.

- **Library / DLL Injection Detection**  
  Scans loaded native libraries, memory maps, and hooks to block cheats early.

- **Root / Debugger / VPN Detection**  
  Identifies rooted devices, attached debuggers, and VPN usage.

- **Unity Integration**  
  Simple C# API for calling native anti-cheat checks at startup.

- **Lightweight & Fast**  
  Written in C++ for minimal performance overhead. Runs before gameplay begins.

---

## 🛠️ Installation

1. Clone or download the repository.
2. Place the provided `libanticheat.so` (or build your own from `src/`) into  
   `Assets/Plugins/Android/arm64-v8a/`.
3. Add the `AntiCheat.cs` script to your Unity project.
4. (Optional) Customize checks — enable/disable root detection, VPN blocking, etc.

---

## 🚀 Usage

Call the anti-cheat at game startup:

```csharp
using UnityEngine;

public class GameInit : MonoBehaviour
{
    void Awake()
    {
        if (!AntiCheat.RunChecks())
        {
            Debug.LogError("Security check failed. Closing game.");
            Application.Quit();
        }
    }
}
