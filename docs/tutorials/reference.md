# Layer and machine values

> **Type:** Reference
> **Orientation:** information
> **Serves:** cognition + work
> **Audience assumption:** practitioner consulting facts

## Interface

Values from `conf/layer.conf`.

| Item | Value |
| --- | --- |
| Collection | `qcom-3rdparty` |
| Layer priority | `5` |
| Layer depends | `core qcom` |
| Compatible series | `wrynose` |
| Recipe glob | `${LAYERDIR}/recipes-*/*/*.bb` and `.bbappend` |
| Dynamic layer | `qcom-distro:${LAYERDIR}/dynamic-layers/qcom-distro/*/*/*.bb{,append}` |

## Parameters

From `conf/machine/uno-q.conf` (Arduino UNO Q). Include: `conf/machine/include/qcom-qcm2290.inc`.

| Variable | Value in source |
| --- | --- |
| `MACHINEOVERRIDES` | prepends `arduino:` |
| `PREFERRED_PROVIDER_virtual/kernel` | `linux-arduino` |
| `PREFERRED_PROVIDER_virtual/bootloader` | `u-boot-arduino` |
| `UBOOT_CONFIG` | `qrb2210-arduino-imola` |
| `QCOM_DTB_DEFAULT` | `qrb2210-arduino-imola` |
| `KERNEL_DEVICETREE` | `qcom/qrb2210-arduino-imola.dtb` |
| `MACHINE_FEATURES` | `efi usbhost usbgadget alsa wifi bluetooth` |
| `QCOM_BOOT_FIRMWARE` | `firmware-qcom-boot-qrb2210-arduino-imola` |
| `QCOM_BOOT_FILES_SUBDIR` | `qrb2210-arduino-imola` |
| `QCOM_PARTITION_FILES_SUBDIR` | `partitions/qrb2210-unoq/emmc-16GB` |

## Behavior

`BBPATH` and `BBFILES` pick up `recipes-*/*/*.bb` and `.bbappend` under this layer. `LAYERSERIES_COMPAT_qcom-3rdparty` is `wrynose`.

## Errors

The `uno-q` machine adds `qbootctl` so the Android bootloader marks the boot successful. Source notes that firmware otherwise switches to slot B and fails to boot.

## Examples

Kas invocation recorded in `docs/index.md`:

```bash
kas build meta-qcom-3rdparty/ci/<machine.yml>
```

Machine YAML files in this repo include `ci/uno-q.yml` and `ci/radxa-dragon-q6a.yml`.

*(see How-to: How to add this layer)*

## Provenance

- `conf/layer.conf`
- `conf/machine/uno-q.conf`
- `docs/index.md`
