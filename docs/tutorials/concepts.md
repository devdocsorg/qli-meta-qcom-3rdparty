# About third-party Qualcomm boards

> **Type:** Explanation
> **Orientation:** understanding
> **Serves:** cognition + study
> **Audience assumption:** reader reflecting away from the work

## Context

Qualcomm-maintained reference boards stay in `meta-qcom`. Third-party and community boards would fragment that layer, so they live here as `meta-qcom-3rdparty`. This fork (`devdocsorg/qli-meta-qcom-3rdparty`) tracks Qualcomm Linux 2.x on `wrynose`.

## Why

A separate collection (`qcom-3rdparty`) keeps Qualcomm-supported hardware in one place and lets vendor machines (`conf/machine`, for example `uno-q.conf` and `radxa-dragon-q6a.conf`) move on their own review cadence.

Branch policy follows that split:

- **main** aims at the newest Yocto release.
- **wrynose** is the LTS line for Qualcomm Linux 2.x (Yocto Project 6.0).
- **scarthgap** and **kirkstone** cover earlier Qualcomm Linux 1.x lines.

Patches should land on `main` first and backport to `wrynose` when possible (`BACKPORTING.md`). The layer depends on `core` and `qcom`. When `qcom-distro` is in the build, `BBFILES_DYNAMIC` also loads `dynamic-layers/qcom-distro`.

## Trade-offs

Splitting third-party machines keeps `meta-qcom` smaller and closer to Qualcomm-supported hardware. The cost is an extra layer and a backport workflow for stable branches.

This is not an official Qualcomm.com publication. Hosted copies of these pages are a DevDocs QLI 2.0 pilot.

## Further reading

- `README.md` (branches and dependencies)
- `BACKPORTING.md`
- `docs/contributing.md`

*(see How-to: How to add this layer)* *(see Reference: layer and machine values)*

## Provenance

- `README.md`
- `conf/layer.conf`
- `docs/index.md`
