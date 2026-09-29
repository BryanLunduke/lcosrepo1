# LCOS 0.7 apt overlay — UNSIGNED staging for editor signing

**Date:** 2026-09-28 (America/Chicago / CDT)
**Status:** UNSIGNED — ready for editor GPG sign. Do **not** push until signed.
**Do not** invent GPG signatures. **Do not** publish unsigned `Release` as the live overlay.
**Do not** use `/workspace/lcos-0.8-apt-staging` for this publish (that tree is LLK-only / stale for 0.7 identity).

## Official ISO

| Field | Value |
|-------|-------|
| Filename | `lcos-live-07-08.iso` |
| Path | `/workspace/lcos-iso/lcos-live-07-08.iso` |
| SHA256 | `c27376f042e3b3153899636b3ffc0eaa9cf44dbe31c8cf56393e78d0a0816cde` |
| Recipe | `/workspace/lcos-live-07/` |
| Suite / component | `excalibur` / `main` |

## Staging paths

| What | Path |
|------|------|
| Staging tree | `/workspace/lcos-0.7-apt-staging/lcosrepo1/` |
| Staging git worktree apt mirror | `/workspace/lcos-0.7-apt-staging/lcosrepo1-git/apt/` |
| Apt root | `/workspace/lcos-0.7-apt-staging/lcosrepo1/apt/` |
| **Unsigned Release** | `/workspace/lcos-0.7-apt-staging/lcosrepo1/apt/dists/excalibur/Release` |
| Unsigned Release (attach copy) | `/workspace/LCOS-excalibur-Release-0.7-UNSIGNED` |
| Recipe packaging mirror | `/workspace/lcos-live-07/packaging/apt-repo/` |
| Pre-ship backup (prior packaging apt-repo) | `/workspace/lcos-live-07/packaging/apt-repo-pre-0.7-ship-backup/` |
| Stale-pool backup (0.6 + LLK lcos7) | `/workspace/lcos-0.7-apt-staging/apt-pool-pre-0.7-official-backup-*/` |
| Seed (authoritative 0.7 overlay set) | `/workspace/lcos-live-07/config/packages.chroot/` |

Layout (unchanged lcosrepo1 practice):

- `pool/main/<letter>/<package>/…deb`
- `dists/excalibur/main/binary-amd64/Packages(.gz)` — all packages in pool
- `dists/excalibur/main/binary-all/Packages(.gz)` — `Architecture: all` only
- `apt-ftparchive-release.conf` — Origin/Label LCOS, Suite/Codename excalibur, Architectures amd64, Components main, Description "LCOS overlay"

Working tree has **no** `InRelease` and **no** `Release.gpg`.

## Contents

- **30** debs from `config/packages.chroot/` (0.7 ship set for `lcos-live-07-08`)
- Custom apps: City **0.7-4**, Edit **0.7-5**, Paint **0.7-1**, About **0.7-1**
- Desktop-config **0.7-7**; `lcos-base` **0.7-2**; other `lcos-*` **0.7-1** (updates **0.7-1**)
- LLK trio **7.2.6-lcos8**
- Full XLibre `25.1.9-1+lcos1` set (incl. vmware `25.0.0-2+lcos1`)
- **Not** included: `linux-libc-dev`; `micropolis` / `micropolis-data` (absent from 07-08 ISO); theme/icon packages removed in 0.5

**Pool deb count: 30**

## Package table (Package, Version, Arch, bytes, SHA256)

| Package | Version | Arch | Bytes | SHA256 |
|---------|---------|------|-------|--------|
| lcos-appimage-thumbnailer | 0.7-1 | all | 3224 | ad354560ed788e8b66f48a3a6b040e5dfc0991e23ba8425e9ea2620b5bcd9b13 |
| lcos-archive-keyring | 0.7-1 | all | 7176 | 3db646fed38ad207b917c6d41ded57f1dd76e9fa373d80c8516118a433bd4b58 |
| lcos-base | 0.7-2 | all | 2704 | f54d779b21aabeb4af9d01d00d1dc9123548c27c273c1678f74004feb773b5d4 |
| lcos-branding | 0.7-1 | all | 8471056 | 925cb43ef7d44a7ba773737ffd5b945dabfcecf20a1de42b2113991b6b4f1f2c |
| lcos-desktop | 0.7-1 | all | 1748 | 502be0bb4a7dc9cce58c9469d2ab17d927b416f009ab70e7a4125dc17c14d809 |
| lcos-desktop-config | 0.7-7 | all | 23536 | 8f3a9eb6bf039105e8c3b2c2885ce8a1969cbf587cb936343bd702ee64943c4d |
| lcos-theme-clearlooks | 0.7-1 | all | 85864 | 585ea557feae1829fcb611e42a328c5b534b3674bf9b1e567444ff3974f2568b |
| lcos-updates | 0.7-1 | amd64 | 157292 | bdf61b8e73255abf7cebae82140955a54970e421a81a1d8a3e1b0687086048f3 |
| lcos-zork | 0.7-1 | all | 156524 | 2a271e9e4a53c4ba224ede696e752388efeef30d6aa0045b4627f119fdcd5b4f |
| linux-headers-7.2.6-lunduke | 7.2.6-lcos8 | amd64 | 9809952 | ead0ffbec6d7d19ff9d542a960c96e0a80007d4b4334813d651101be375588a2 |
| linux-image-7.2.6-lunduke | 7.2.6-lcos8 | amd64 | 30084852 | ce726d07fcf717405a0b99bca6124613e228916d8b1104915c9b3e1519c91dd7 |
| lunduke-about | 0.7-1 | amd64 | 331940 | 4e6981039e45568ddc6f90b9c0466411e0e6defa87f94f41397bff1798b8e7a8 |
| lunduke-city | 0.7-4 | amd64 | 1822252 | a0e1d2f503d1d8a162fe0fbd7077a8a065e938359f98aa67dddfcc8b4948b874 |
| lunduke-edit | 0.7-5 | amd64 | 232096 | fc055fea9ee5826476a3efdfba1e080e5e95d6242a3772d980e2a3bc70b7bf8a |
| lunduke-linux-kernel | 7.2.6-lcos8 | all | 1608 | d15931ef4322e857a5ee0a3bf859afef615c2d797ebf5374c97bfef7d48cead1 |
| lunduke-paint | 0.7-1 | amd64 | 647500 | f5b445fefc37e41e6655ffda0764aa4c8c064d27f734ab5aa04cf68a9cebfae6 |
| xlibre | 1:25.1.9-1+lcos1 | amd64 | 1476 | e0d8ddda1cda7493aff3ef736176238b747469890cb9b8dd98929c6e420f274c |
| xlibre-x11-common | 1:25.1.9-1+lcos1 | all | 18392 | 2f977684848deb6861d1d85cbbcc53a5d0c993f950f428ac45e6420355c15156 |
| xserver-xlibre | 1:25.1.9-1+lcos1 | amd64 | 1380 | a460c0c5ace3e037ebf3edff1717c1fbcfdaaeb198edb37ad3403fb2c7217760 |
| xserver-xlibre-common | 2:25.1.9-1+lcos1 | all | 16488 | 476bb5fcc91db89958811388c7c0992fb0b49b8110b19b4eecad14e5b5f2ad0a |
| xserver-xlibre-core | 2:25.1.9-1+lcos1 | amd64 | 1553512 | e34b86d703cf851988f799f9bd125ad98a48a5ff28bdfe459010806cbb2f3821 |
| xserver-xlibre-input-all | 1:25.1.9-1+lcos1 | amd64 | 1372 | f9f97b32ea398c363f9f844b4a91cca1b958207535b7ecbcf49277c0c709b77d |
| xserver-xlibre-input-libinput | 25.0.1-1+lcos1 | amd64 | 43408 | 117afb33c0bbc2ac538beed60db7cea17b2b8425a08fcc1d6f41ce45f87ea2ec |
| xserver-xlibre-video-all | 1:25.1.9-1+lcos1 | amd64 | 1416 | ee84ab83cb0a757325f3cbb45d6696b5cfc4e088dedc465eb77305f01e108fbb |
| xserver-xlibre-video-amdgpu | 25.1.2-1+lcos1 | amd64 | 71612 | 3e03da6ec399fadcf588f55f61504b3fc13124cbd770b153811b8afbd2bd5c67 |
| xserver-xlibre-video-ati | 1:25.0.1-1+lcos1 | amd64 | 146972 | d6dbccaea6995a0fb88fa3c0f4efd4aef92bbf4d384672ef40195c88831f421a |
| xserver-xlibre-video-fbdev | 1:25.0.0-1+lcos1 | amd64 | 10400 | d3e287036d8ec34495e8b261e72b7781d99a5331937c73c466d8db66a2b66389 |
| xserver-xlibre-video-nouveau | 1:25.0.1-1+lcos1 | amd64 | 85232 | b9d8acb02f60f8c9dcd74d6adcf7d27558b5e29ba53cbbb8e7eab8473ebd027d |
| xserver-xlibre-video-vesa | 1:25.0.0-1+lcos1 | amd64 | 12708 | 6edf0cfd6c242759592e23b8bd74594fd320e12aa31c2f5f45fb09823a1c08e9 |
| xserver-xlibre-video-vmware | 1:25.0.0-2+lcos1 | amd64 | 72620 | a5a920a8ad076458e06e5d5b7304e64856477e4a0d2fa75f1830c0d129ca6011 |

## Unsigned Release

- Path (in tree): `/workspace/lcos-0.7-apt-staging/lcosrepo1/apt/dists/excalibur/Release`
- Path (attach): `/workspace/LCOS-excalibur-Release-0.7-UNSIGNED`
- SHA256: `dc98cf015cc9b9cd65fea26b022f7046287ba865fc0cea375fc458844b40c406`
- Bytes: 2366

## Editor signing commands (prior method — same as 0.6)

Fingerprint: `5A01D4BDCDD1E1531D456A7560D6E7F6CBD6D572`
UID: LCOS Archive Signing Key `<lcos@lunduke.com>`

```bash
cd /workspace/lcos-0.7-apt-staging/lcosrepo1/apt/dists/excalibur

gpg --default-key 5A01D4BDCDD1E1531D456A7560D6E7F6CBD6D572 \
  --clearsign -o InRelease Release

gpg --default-key 5A01D4BDCDD1E1531D456A7560D6E7F6CBD6D572 \
  --armor --detach-sign -o Release.gpg Release
```

Then verify:

```bash
gpg --verify InRelease
gpg --verify Release.gpg Release
```

After signing, mirror signatures into:

- `/workspace/lcos-live-07/packaging/apt-repo/dists/excalibur/`
- `/workspace/lcos-0.7-apt-staging/lcosrepo1-git/apt/dists/excalibur/` (if using the git worktree)

## Publish target (after sign only)

- Repo: `BryanLunduke/lcosrepo1` (GitHub Pages)
- Public URL: `https://lcos.lunduke.com/apt`
- Suggested commit message: `Publish LCOS 0.7 overlay (excalibur/main) — packages.chroot 0.7: City 0.7-4, Edit 0.7-5, Paint 0.7-1, About 0.7-1, desktop-config 0.7-7, LLK 7.2.6-lcos8`

**Do not push until signed.** Chloe/Ted publish after editor signs.

## PackageSourceList handoff

- `/workspace/LCOS-07-PackageSourceList.md` — ready for Ted to CopyFromBox / attach for editor download.
