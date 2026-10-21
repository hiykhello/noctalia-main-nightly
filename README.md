# noctalia-main-nightly

Automated GitHub Actions builder for [Noctalia](https://github.com/noctalia-dev/noctalia) (`main` branch) for Arch Linux / CachyOS.

## Features
- **Zero Local Compilation**: Built via GitHub Actions with 16GB RAM cloud runners.
- **Daily Nightly Builds**: Automatically builds daily at 04:00 AM (UTC+8) and on manual dispatch.
- **Full Arch Package**: Generates real `*.pkg.tar.zst` packages managed cleanly by `pacman`.

## How to Install / Update

### 1. One-line Direct Install (Fastest)
```bash
run0 pacman -U "https://github.com/shenbeng/noctalia-main-nightly/releases/download/nightly/noctalia-git-latest-x86_64.pkg.tar.zst"
```

### 2. Via AUR helper (paru)
```bash
git clone https://github.com/shenbeng/noctalia-main-nightly.git
cd noctalia-main-nightly
paru -Bi .
```
