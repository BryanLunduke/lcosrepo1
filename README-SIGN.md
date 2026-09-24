# LCOS apt overlay — LLK 7.2.6-lcos5 UNSIGNED staging for editor signing

**Date:** 2026-09-24 (America/Chicago / CDT)
**Status:** UNSIGNED — ready for editor GPG sign. Do **not** push until signed.
**Do not** invent GPG signatures. **Do not** publish unsigned `Release` as the live overlay.

## Why

Fixes Doug Burks iptables bug on optional Lunduke Linux Kernel:
- iptables-nft: `Could not fetch rule set generation id: Invalid argument`
- iptables-legacy: `Module ip_tables not found`

Root cause in lcos4: `CONFIG_NETFILTER_ADVANCED` / `CONFIG_NF_TABLES` / `IP_NF_FILTER` incomplete.
lcos5 enables Distro-like netfilter (nft + legacy xtables modules).

## Staging paths

| What | Path |
|------|------|
| Staging tree (rsync) | `/workspace/lcos-0.7-apt-staging/lcosrepo1/` |
| Staging git worktree (local branch) | `/workspace/lcos-0.7-apt-staging/lcosrepo1-git/` |
| Apt root | `…/apt/` |
| **Unsigned Release** | `…/apt/dists/excalibur/Release` |
| Local git branch | `staging-llk-7.2.6-lcos5` (NOT pushed) |

Base: LCOS 0.6 overlay pool + indexes, with LLK trio replaced **lcos4 → lcos5**.
`InRelease` / `Release.gpg` removed — editor must re-sign.

**Not** included: `linux-libc-dev` (would conflict with Distro; not needed for LLK boot).

## New LLK packages (Package, Version, Arch, bytes, SHA256)

| Package | Version | Arch | Bytes | SHA256 |
|---------|---------|------|-------|--------|
| linux-image-7.2.6-lunduke | 7.2.6-lcos5 | amd64 | 24543396 | 8267f48465539959d67e9a48d7f7e14199d8fc772bce4f040cd676d375b87a71 |
| linux-headers-7.2.6-lunduke | 7.2.6-lcos5 | amd64 | 9782312 | 88b114afa6da15808ceeeb7dabb36ac6d7abe19f6cd07f46e0b1fcf7bec6e19c |
| lunduke-linux-kernel | 7.2.6-lcos5 | all | 1476 | b7621ad2b20bff9f3c963707afc12e663b9923512198b8a4dd96477344f98255 |

Pool deb count: **30** (same as 0.6 overlay set; LLK versions bumped).

## Unsigned Release

- Path: `/workspace/lcos-0.7-apt-staging/lcosrepo1/apt/dists/excalibur/Release`
- SHA256: `50ede988152994f403d14d1d58279daa444f76c9c19119b169fa12d383a0b806`

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
`staging-llk-7.2.6-lcos5` after sign). Suggested message:
`Publish LLK 7.2.6-lcos5 (netfilter/iptables fix) optional overlay.`

**Do not push until signed.**

## User install (after publish)

```bash
sudo apt update
sudo apt install lunduke-linux-kernel
```

Reboot → pick **7.2.6-lunduke** in GRUB. Then `iptables -nvL` / iptables-legacy should work.
