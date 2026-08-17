# Getting started

> **Type:** Tutorial
> **Orientation:** learning
> **Serves:** action + study
> **Audience assumption:** beginner with no prior familiarity

In this tutorial, we will add `meta-qcom-3rdparty` on branch `wrynose` to a Yocto workspace and start a kas build for the Arduino UNO Q machine.

## What we will do

We will confirm the two sibling layers, add this layer after `meta-qcom`, pick the `uno-q` machine, and run the kas one-liner from this repo.

## Start here

We need a Yocto Project 6.0 (`wrynose`) workspace with:

- `openembedded-core` (`meta`) on `wrynose`
- `meta-qcom` on `wrynose`
- [kas](https://kas.readthedocs.io/)

Open a terminal in the workspace root.

## Steps

1. Add `meta-qcom-3rdparty` to `bblayers.conf` after `meta-qcom`.
2. Open `conf/layer.conf` in this layer. You will notice `LAYERSERIES_COMPAT_qcom-3rdparty = "wrynose"`.
3. Open `conf/machine/uno-q.conf`. You will notice `KERNEL_DEVICETREE` and `MACHINE_FEATURES` for the Arduino UNO Q.
4. Run:

```bash
kas build meta-qcom-3rdparty/ci/uno-q.yml
```

5. The output should look like a kas/BitBake build starting for machine `uno-q`. If kas cannot find the YAML file, we are not at the workspace root that contains this layer.

## What we accomplished

We attached a third-party Qualcomm BSP layer on the Qualcomm Linux 2.x (`wrynose`) line and kicked off the UNO Q image build. *(see How-to: How to add this layer)* *(see Reference: layer and machine values)* *(see Explanation: About third-party boards)*

## Provenance

- `README.md`
- `docs/index.md`
- `conf/layer.conf`
- `conf/machine/uno-q.conf`
