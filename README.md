# Snapcraft builder

This docker project is intended to provide an image that you can use to build snap packages (https://snapcraft.io) within a docker container.

In order to build this, you just need to execute:

```bash
docker run --rm -v $(PWD):/app -w /app patrcloud/snapcraft-builder:core20 snapcraft
```

These images are based on the latest `stable` release of snapcraft. You can change this and build your own Docker image by updating the `RISK` `ARG` in the `Dockerfile`.
The `RISK` argument can be one of: `stable`, `candidate`, `beta`, `edge`.

The following tags are available:

`core20` - Based on Ubuntu 20.04 Focal Fossa
`core18` - Based on Ubuntu 18.04 Bionic Beaver
`core` - Based on Ubuntu 16.04 Xenial Xerus

While any Ubuntu version can work with just the right `base` set in the `snapcraft.yml` file, we've based each tag on the corresponding Ubuntu version in order to provide a consistent GLIBC version for each base. That being said, all of the images contain all the `core`, `core18` as well as `core20` base.

You can also run specific snapcraft build steps by changing the argument passed to the `snapcraft` command.

```bash
docker run --rm -v $(PWD):/app -w /app patrcloud/snapcraft-builder:core20 snapcraft build
docker run --rm -v $(PWD):/app -w /app patrcloud/snapcraft-builder:core20 snapcraft prime
docker run --rm -v $(PWD):/app -w /app patrcloud/snapcraft-builder:core20 snapcraft stage
```

We at Patr (https://patr.cloud) use this primarily to build the snap packages of our CLI (`sudo snap install patr --channel=edge`), but we're more than happy to support the community with any help that they may require. If you're facing any issues with this snap, please open an issue and we'll get it fixed.

Happy snapping!
