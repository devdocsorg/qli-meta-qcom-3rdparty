# How to add this layer

> **Type:** How-to guide
> **Orientation:** task
> **Serves:** action + work
> **Audience assumption:** competent practitioner mid-task

## Goal

Add `meta-qcom-3rdparty` to an existing `wrynose` OpenEmbedded workspace and build one third-party Qualcomm machine image.

## Conditions

- The workspace already has `openembedded-core` (`meta`) and `meta-qcom` on `wrynose`.
- You know the machine name under `conf/machine` (for example `uno-q` or `radxa-dragon-q6a`).
- Official Qualcomm reference boards stay in `meta-qcom`, not this layer. *(see Explanation: About third-party boards)*

## Procedure

1. Clone or update this layer on `wrynose`.
2. Append the layer path to `bblayers.conf` after `meta-qcom`.
3. If you want a kas-driven build, run `kas build meta-qcom-3rdparty/ci/<machine>.yml`. Example files in this repo: `ci/uno-q.yml`, `ci/radxa-dragon-q6a.yml`.
4. If you want a BitBake-only build, set `MACHINE` to the config basename (for example `uno-q`) and build your image recipe as you already do.

## Verification

- `bitbake-layers show-layers` lists `meta-qcom-3rdparty`.
- `conf/layer.conf` still has `LAYERSERIES_COMPAT_qcom-3rdparty = "wrynose"`.
- The chosen `conf/machine/<machine>.conf` exists.

## Failures

- **Layer not found:** the path in `bblayers.conf` is wrong.
- **Incompatible series:** you are not on `wrynose`. Do not mix this checkout with `scarthgap` or `kirkstone` without the matching branch. *(see Explanation: About third-party boards)*
- **Missing `meta-qcom`:** this layer depends on collection `qcom`. Add `meta-qcom` first.

*(see Tutorial: Getting started)* *(see Reference: layer and machine values)*
