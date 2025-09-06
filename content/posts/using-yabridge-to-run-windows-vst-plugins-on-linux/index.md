+++
date = '2025-03-20T22:38:09+08:00'
draft = false
title = 'Using Yabridge to Run Windows Vst Plugins on Linux'
+++



`yabridge` is a powerful tool that allows you to use Windows VST2 and VST3 plugins seamlessly on Linux through [Wine]({{< relref "posts/what-is-wine/index.md" >}}). Here's how I set it up.

## Prerequisites

Make sure you have the following installed:

- Wine (preferably `wine-staging`)
- `yabridge`
- A VST-compatible DAW (e.g. REAPER)
- `winetricks` (optional but useful)
- Wine installed in a 64-bit prefix

### On Arch Linux:

You can install these via the AUR helper such as yay:

```bash
yay -S wine-staging yabridge yabridgectl winetricks
```

## 1. Prepare Your Wine Prefix

Create and configure a clean 64-bit Wine prefix:
*(You can replace `.wine` with any name you prefer for isolation)*

```bash
WINEPREFIX=~/.wine WINEARCH=win64 wineboot
```

Optionally, install dependencies for certain plugins:

```bash
WINEPREFIX=~/.wine winetricks corefonts vcrun2015
```

## 2. Install Your Windows VST Plugins

Install your VST2/VST3 plugins into the Wine prefix:

- VST2 typically go into:  
  `~/.wine/drive_c/Program Files/VstPlugins/`

- VST3 go into:  
  `~/.wine/drive_c/Program Files/Common Files/VST3/`

Make sure the plugins are properly installed inside your Wine environment.

## 3. Configure yabridge

Register your plugin directories with `yabridgectl`:

```bash
yabridgectl add "~/.wine/drive_c/Program Files/VstPlugins"
yabridgectl add "~/.wine/drive_c/Program Files/Common Files/VST3"
```

Here are my list of directories in yabridge:
```bash
❯ yabridgectl list
/home/momo/.wine/drive_c/Program Files/Common Files/VST2
/home/momo/.wine/drive_c/Program Files/Common Files/VST3
/home/momo/.wine/drive_c/Program Files/Common Files/VstPlugins
/home/momo/.wine/drive_c/Program Files/Steinberg/VSTPlugins
/home/momo/.wine/drive_c/Program Files/VstPlugins
/home/momo/.wine/drive_c/Program Files (x86)/VSTPlugins
/home/momo/.wine/drive_c/VST64
/home/momo/.wine-spitfire/drive_c/Program Files/Common Files/VST3
```

Then synchronize:

```bash
yabridgectl sync
```

This step bridges the Windows plugins into `.vst/` and `.vst3/` directories under `~/.vst/` and `~/.vst3/` respectively, which Linux-native DAWs can scan.

## 4. Set Plugin Paths in Your DAW

In your Linux DAW (e.g. REAPER):

1. Go to Preferences → Plug-ins → VST.
2. Add the following directories:
   - `~/.vst`
   - `~/.vst3`
3. Rescan for plugins.

You should now see your Windows VST plugins available in your Linux DAW as if they were native.
![](./keyzone.png)


---

> ℹ️ Note: Some plugins might require additional libraries or fonts through `winetricks` depending on their vendor.


## Known Issues and Fixes (from yabridge)

If you're encountering issues with certain plugins, be sure to check the official [Known Issues and Fixes section](https://github.com/robbert-vdh/yabridge?tab=readme-ov-file#known-issues-and-fixes) of the yabridge README. It provides:

- Workarounds for problematic plugins
- Tips for bridging compatibility
- Environment variable tweaks (e.g. fixing UI scaling, crashes)

Always refer to this when something doesn’t behave as expected — many plugin-specific problems have already been documented there.
