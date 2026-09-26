# LCOS apt overlay — LLK 7.2.6-lcos7 UNSIGNED staging for editor signing

**Date:** 2026-09-25 (America/Chicago / CDT)
**Status:** UNSIGNED — ready for editor GPG sign. Do **not** push until signed.
**Do not** invent GPG signatures. **Do not** publish unsigned `Release` as the live overlay.

## Why

HW modules pass on optional Lunduke Linux Kernel (audio / Wi-Fi / BT / UVC / HID / IGC),
building on prior lcos5 netfilter+uinput work.

lcos7 includes:
- Prior lcos5: Distro-like netfilter (nft + legacy xtables) + uinput
- HW module pass: audio (snd-usb-audio, SOF, Realtek HDA via per-ALC modules),
  Wi-Fi (iwlwifi, rtw88/rtw89, ath9k/10k/11k, brcmfmac, mt7921e, rtl8xxxu),
  Bluetooth (bluetooth, btusb), UVC (uvcvideo), HID (i2c-hid-acpi, hid-multitouch),
  Ethernet (igc, igb)

## Staging paths

| What | Path |
|------|------|
| Staging tree (rsync) | `/workspace/lcos-0.7-apt-staging/lcosrepo1/` |
| Staging git worktree (local branch) | `/workspace/lcos-0.7-apt-staging/lcosrepo1-git/` |
| Apt root | `…/apt/` |
| **Unsigned Release** (in tree) | `…/apt/dists/excalibur/Release` |
| **Unsigned Release** (attach copy) | `/workspace/LCOS-excalibur-Release-llk-lcos7-UNSIGNED` |
| Local git branch | `staging-llk-7.2.6-lcos7` (NOT pushed) |

Base: live `BryanLunduke/lcosrepo1` master (LLK lcos5) with LLK trio replaced **lcos5 → lcos7**.
`InRelease` / `Release.gpg` removed — editor must re-sign.

**Not** included: `linux-libc-dev` (would conflict with Distro; not needed for LLK boot).

## New LLK packages (Package, Version, Arch, bytes, SHA256)

| Package | Version | Arch | Bytes | SHA256 |
|---------|---------|------|-------|--------|
| linux-image-7.2.6-lunduke | 7.2.6-lcos7 | amd64 | 30020124 | f16d3e5c89b74dc012ef31e7f5cc10e1c36953f92bdc83c5ea1250652b6af9ed |
| linux-headers-7.2.6-lunduke | 7.2.6-lcos7 | amd64 | 9809304 | 1997bf4355ad9d15fa2a8e3d4ee99a41d66522d28bcb2475c14486f50ba56826 |
| lunduke-linux-kernel | 7.2.6-lcos7 | all | 1540 | dcedad08027d742ded91ccac478c666ed974a7d4bfd8a55e104e457b75f77a4d |

Pool deb count: **30** (same as 0.6 overlay set; LLK versions bumped).

## Unsigned Release

- Path (in tree): `/workspace/lcos-0.7-apt-staging/lcosrepo1/apt/dists/excalibur/Release`
- Path (attach): `/workspace/LCOS-excalibur-Release-llk-lcos7-UNSIGNED`
- SHA256: `0495a2573911361e8b4378afa140a1298519ae161b90921576e3fe63ee0b6e34`

## Editor signing commands

Fingerprint: `5A01D4BDCDD1E1531D456A7560D6E7F6CBD6D572`
UID: LCOS Archive Signing Key `<lcos@lunduke.com>`

```bash
cd /workspace/lcos-0.7-apt-staging/lcosrepo1/apt/dists/excalibur

gpg --default-key 5A01D4BDCDD1E1531D456A7560D6E7F6CBD6D572 \
  --clearsign -o InRelease Release

gpg --default-key 5A01D4BDCDD1E1531D456A7560D6E7F6CBD6D572 \
  --armor --detach-sign -o Release.gpg Release
```

Then commit+push **master** of `BryanLunduke/lcosrepo1` (or merge local branch
`staging-llk-7.2.6-lcos7` after sign). Suggested message:
`Publish LLK 7.2.6-lcos7 (HW modules: audio/Wi-Fi/BT/UVC/HID/IGC; prior netfilter+uinput) optional overlay.`

**Do not push until signed.**

## User install (after publish)

```bash
sudo apt update
sudo apt install lunduke-linux-kernel
```

Reboot → pick **7.2.6-lunduke** in GRUB.
