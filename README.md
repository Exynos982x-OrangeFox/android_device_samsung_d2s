# OrangeFox Recovery device tree for the Samsung Galaxy Note10+ (d2s)

| Device | Samsung Galaxy Note10+ |
| :-- | :-- |
| Codename | d2s |
| Models | SM-N975F, SM-N975F/DS |
| SoC | Exynos 9825 |

Common tree: [android_device_samsung_exynos9820-common](https://github.com/Exynos982x-OrangeFox/android_device_samsung_exynos9820-common)

## Kernel

The prebuilt `Image` and `dtbo.img` are extracted from the official LineageOS 23.2 `recovery.img` of
2026-10-25 (sha256 `3e3b61971989bf0665b0ffa5e1702e329b767b0efdd44f43145c33b52a602f5a`), built from
[android_kernel_samsung_exynos9820](https://github.com/LineageOS/android_kernel_samsung_exynos9820/tree/a412cfaf86b980ce35cae96a35f678c8ea551575)
with `exynos9820-d2s_defconfig`.

## Building

```sh
git clone https://gitlab.com/OrangeFox/sync.git
cd sync
./orangefox_sync.sh --branch 12.1 --path ~/fox_12.1

cd ~/fox_12.1
git clone -b fox_12.1 https://github.com/Exynos982x-OrangeFox/android_device_samsung_d2s device/samsung/d2s
git clone -b fox_12.1 https://github.com/Exynos982x-OrangeFox/android_device_samsung_exynos9820-common device/samsung/exynos9820-common

export FOX_BUILD_DEVICE=d2s
source build/envsetup.sh
lunch twrp_d2s-eng
mka adbd recoveryimage
```

The recovery image is written to `out/target/product/d2s/`, along with an Odin-flashable `.tar`.
