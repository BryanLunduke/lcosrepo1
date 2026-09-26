# LCOS apt overlay — LLK 7.2.6-lcos8 UNSIGNED staging for editor signing

**Date:** 2026-09-26 (America/Chicago / CDT)
**Status:** UNSIGNED — ready for editor GPG sign. Do **not** push until signed.
**Do not** invent GPG signatures. **Do not** publish unsigned `Release` as the live overlay.

## Why

lcos8 adds RTL8187/RTL8187B USB Wi-Fi (GitHub LCOS#81) on top of the
lcos7 high-impact HW module set (audio / Wi-Fi / BT / UVC / HID / IGC)
and prior lcos5 netfilter+uinput work.

## Staging paths

| What | Path |
|------|------|
| Staging tree (rsync) | `/workspace/lcos-0.8-apt-staging/lcosrepo1/` |
| Staging git worktree (local branch) | `/workspace/lcos-0.8-apt-staging/lcosrepo1-git/` |
| Apt root | `…/apt/` |
| **Unsigned Release** (in tree) | `…/apt/dists/excalibur/Release` |
| **Unsigned Release** (attach copy) | `/workspace/LCOS-excalibur-Release-llk-lcos8-UNSIGNED` |
| Local git branch | `staging-llk-7.2.6-lcos8` (NOT pushed) |

Base: live `BryanLunduke/lcosrepo1` master (LLK lcos7) with LLK trio replaced **lcos7 → lcos8**.
`InRelease` / `Release.gpg` removed — editor must re-sign.

**Not** included: `linux-libc-dev` (would conflict with Distro; not needed for LLK boot).

## New LLK packages (Package, Version, Arch, bytes, SHA256)

| Package | Version | Arch | Bytes | SHA256 |
|---------|---------|------|-------|--------|
| linux-image-7.2.6-lunduke | 7.2.6-lcos8 | amd64 | 30084852 | ce726d07fcf717405a0b99bca6124613e228916d8b1104915c9b3e1519c91dd7 |
| linux-headers-7.2.6-lunduke | 7.2.6-lcos8 | amd64 | 9809952 | ead0ffbec6d7d19ff9d542a960c96e0a80007d4b4334813d651101be375588a2 |
| lunduke-linux-kernel | 7.2.6-lcos8 | all | 1608 | d15931ef4322e857a5ee0a3bf859afef615c2d797ebf5374c97bfef7d48cead1 |

Pool deb count: **30** (same as 0.7 overlay set; LLK versions bumped).

## Unsigned Release

- Path (in tree): `/workspace/lcos-0.8-apt-staging/lcosrepo1/apt/dists/excalibur/Release`
- Path (attach): `/workspace/LCOS-excalibur-Release-llk-lcos8-UNSIGNED`
- SHA256: `7603940d958da72cc62cc729d1c7add5562c076838f91d5050120719e4166f8e`

## Editor signing commands

Fingerprint: `5A01D4BDCDD1E1531D456A7560D6E7F6CBD6D572`
UID: LCOS Archive Signing Key `<lcos@lunduke.com>`

```bash
cd /workspace/lcos-0.8-apt-staging/lcosrepo1/apt/dists/excalibur

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

Then commit+push **master** of `BryanLunduke/lcosrepo1` (or merge local branch
`staging-llk-7.2.6-lcos8` after sign). Suggested message:
`Publish LLK 7.2.6-lcos8 (RTL8187 USB Wi-Fi; prior HW modules + netfilter+uinput) optional overlay.`

**Do not push until signed.**

## User install (after publish)

```bash
sudo apt update && sudo apt install --reinstall lunduke-linux-kernel
```

(or `sudo apt upgrade`). Reboot → pick **7.2.6-lunduke** in GRUB.
