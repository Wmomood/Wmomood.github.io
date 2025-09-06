+++
date = '2025-04-17T02:30:19+08:00'
draft = true
title = 'Terminal Music Player'
+++

## Prepare

```
TerminalMusicPlayer/
├── CMakeLists.txt
├── include/
│   └── Metadata/MusicScanner.hpp
├── src/
│   ├── main.cpp
│   └── Metadata/MusicScanner.cpp
└── build/


```
sudo pacman -S --needed base-devel cmake git sqlite taglib mpv
yay -S ftxui

mkdir -p TerminalMusicPlayer/{include,src,assets,data}
cd TerminalMusicPlayer

git init
touch CMakeLists.txt
```


build test
```
cmake -S . -B build
cmake --build build
./build/music-player
  
```







