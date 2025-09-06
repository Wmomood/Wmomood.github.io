+++
date = '2025-03-20T22:41:08+08:00'
draft = false
title = 'What Is Wine'
+++


**Wine** stands for **"Wine Is Not an Emulator"**. It is a compatibility layer that allows you to **run Windows applications on Linux, macOS, and BSD** without needing a full Windows OS or a virtual machine.

---

## Key Features

- **Runs native Windows apps** on POSIX-compliant systems
- **No virtualization**: runs programs at near-native performance
- Can integrate with **Wine prefixes** (separate environments for apps)
- Works with tools like `winetricks`, `proton`, `yabridge`, and more

---

## Typical Wine Paths

| Component      | Default Path |
|----------------|--------------|
| Wine Prefix    | `~/.wine/`   |
| C Drive        | `~/.wine/drive_c/` |
| Installed Apps | `~/.wine/drive_c/Program Files/` |

You can use custom prefixes like `~/.wine-vst64` for isolating environments.

---

## Basic Usage

```bash
# Run a Windows installer
wine setup.exe

# Run a program already installed
wine "C:\Program Files\App\app.exe"
```

> Tip: Always use quotes around Windows-style paths.

---

## Setup a Clean 64-bit Wine Prefix

```bash
WINEPREFIX=~/.wine-new WINEARCH=win64 wineboot
```

---

## Extend Wine with:

- **winetricks** – install Windows DLLs or fonts
- [**yabridge**]({{< relref "posts/using-yabridge-to-run-windows-vst-plugins-on-linux/index.md" >}}) – bridge Windows VST plugins to Linux DAWs
- **Proton** – Valve’s Wine fork optimized for gaming (used by Steam)

---

## More Info

- Official site: [https://www.winehq.org](https://www.winehq.org)
- App compatibility: [https://appdb.winehq.org](https://appdb.winehq.org)
