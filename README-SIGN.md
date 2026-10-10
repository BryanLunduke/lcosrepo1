# LCOS 0.9.2 AMD GPU overlay additions — UNSIGNED staging (2026-10-09 CT)

Base: lcosrepo1 master 0886afb (published 0.9.1 overlay). Branch staging-0.9.2-amd-gpu, local only. Adds 13 debs from Devuan excalibur-backports (pkgmaster.devuan.org/merged), SHA256-verified against Packages.xz, whose hash matched the InRelease (Good signature: Devuan Release Signing (Excalibur), 9F8D 6C74 DE66 1075 FD17 1BE3 B398 2868 D104 092C).
Unsigned Release: apt/dists/excalibur/Release = /workspace/LCOS-excalibur-Release-0.9.2-amd-UNSIGNED, SHA256 af87f66c6bfd2e8a0bb5f6f3b3d8ae8ad7f33ada57aa2c129589639b29fa9987. InRelease/Release.gpg removed. Do not push until signed.

| Package | Version | Bytes | SHA256 |
|---|---|---|---|
| firmware-amd-graphics | 20260810-1~bpo13+1 | 15983424 | 1142a4da4590f3628bbefb08a3042fb9aa31b865d556ba5894cf80d9f9aa1547 |
| firmware-linux-nonfree | 20260810-1~bpo13+1 | 86500 | 19fa414b01dd64eeb6335a3019324a9c610286cfb3ff9535592e83a0fcdca8ff |
| firmware-linux | 20260810-1~bpo13+1 | 86480 | 7fb08c1ad5e0564f7f4ced5c9cdf0225b4ec081eb42ebcc5ff4e3498955ce29d |
| firmware-misc-nonfree | 20260810-1~bpo13+1 | 5814768 | 647909b648e55e290bc0fdcd6639dba1754c53296221209273aa89f77a8041d8 |
| libegl-mesa0 | 26.1.6-1~bpo13+1 | 139132 | 0d175df6a4fac09eeedfaa9326da1c05c0e8a1911aa413281eb3e3a64ec09b28 |
| libgbm1 | 26.1.6-1~bpo13+1 | 61528 | cfe9a2d49fe55618f921e7ca02e41241376ba843d598f209bfbb65e6058c49a8 |
| libgl1-mesa-dri | 26.1.6-1~bpo13+1 | 51404 | 489f584bab1b3dcf09928a6e918e84c33296340f778286efde6d47357de800c1 |
| libglx-mesa0 | 26.1.6-1~bpo13+1 | 131680 | d6997367ca79b56b882f77d859f73b075c29c975f0f5ead667269eb48cc733be |
| mesa-libgallium | 26.1.6-1~bpo13+1 | 11073632 | 059b19b15ed2fc684e9c03449a4821de0470fe791b947c5d10d4605da1804ac1 |
| mesa-opencl-icd | 26.1.6-1~bpo13+1 | 10144444 | 1adb18bc0b7f54f9bc8039263251f394cdc395c6beaa2637b84c4050f3f29f33 |
| mesa-va-drivers | 26.1.6-1~bpo13+1 | 21856 | fa5deed6639ddd0799579ddcd941541013434d5bd5da8f78a85a182d6d5577e1 |
| mesa-vdpau-drivers | 26.1.6-1~bpo13+1 | 21860 | 98b03a505d1357b8faf2b3b0003776fe78660d8b8d3486eb870b8d110e4d8cb7 |
| mesa-vulkan-drivers | 26.1.6-1~bpo13+1 | 19718352 | e2d4a843b8c55ed17c1e8856805f67b553b013b6ce5f15faeec4db7d4d38ff90 |

Signing: same commands as the 0.9.1 README-SIGN.md, using this Release.
