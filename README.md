# docker-zig

A lightweight Docker image based on Alpine Linux for building and testing [Zig](https://ziglang.org/) projects. It supports both official release versions and in-development builds of the Zig compiler. The image is published to Docker Hub as `shmolyneaux/ziglang` and built automatically via Drone CI.

## Usage

Build an image with an official Zig release:

```sh
docker build . --build-arg VERSION=0.8.0
```

Build an image with an in-development Zig version:

```sh
docker build . --build-arg DEV_BUILD=0.9.0-dev.1139+affd8f8b5
```

Run the Zig compiler inside the container:

```sh
docker run --rm shmolyneaux/ziglang:0.9.0-dev.1139 zig version
```

## Features

- **Alpine-based** — minimal image size.
- **Release builds** — specify any released Zig version via the `VERSION` build arg (default `0.7.1`).
- **Dev builds** — specify any in-development Zig version via the `DEV_BUILD` build arg, which downloads from `ziglang.org/builds`.
- **CI/CD** — automated Docker Hub publishing on push via Drone CI.

## Limitations

- Only supports **linux-x86_64** Zig binaries.
- No pre-installed system libraries beyond what Alpine provides — projects with C dependencies may need additional packages.
- The default `VERSION` build arg may not reflect the latest Zig release; always specify your desired version explicitly.

## History

Development on docker-zig started 2021-07-30, and largely stopped on 2021-09-21:

- **2021-07-30** — Initial commit with Dockerfile (Zig 0.7.1 default), Drone CI pipeline for building and pushing the `0.8.0` release image, LICENSE (MIT), and README.
- **2021-07-30** — Fixed Drone CI build args syntax.
- **2021-09-21** — Added support for in-development (dev) Zig builds via a new `DEV_BUILD` build arg; updated Drone pipeline to build `0.9.0-dev.1139`.
- **2021-09-21** — Updated README with usage instructions for both release and dev builds.
