# tomat (AUR)

AUR package for [tomat](https://github.com/jolars/tomat) - A Pomodoro timer with daemon support for waybar.

## Installation

```bash
# Using an AUR helper (yay, paru, etc.)
yay -S tomat

# Manual installation
git clone https://aur.archlinux.org/tomat.git
cd tomat
makepkg -si
```

## Updating

After each release of tomat:

1. Update `pkgver` in PKGBUILD
2. Download the tarball and compute checksum:
   ```bash
   wget https://github.com/jolars/tomat/archive/v2.8.0.tar.gz
   sha256sum v2.8.0.tar.gz
   ```
3. Update `sha256sums` in PKGBUILD
4. Test build: `makepkg -si`
5. Update `.SRCINFO`: `makepkg --printsrcinfo > .SRCINFO`
6. Commit and push to AUR

## Automation

This repo has a GitHub Action that can automatically create PRs when new releases are published.
See `.github/workflows/update-pkgbuild.yml`.
