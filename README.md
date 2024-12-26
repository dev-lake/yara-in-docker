# yara with docker

This is a Project to help you compile and run Yara as soon as possible.

## How to build image

```bash
docker build -f Dockerfile.build -t yara-builder .
docker build -f Dockerfile.run --build-arg YARA_VERSION=4.5.2 -t yara-run .
docker build -f Dockerfile.godev -t yara-dev .

Optional build arg for Dockerfile.dev:
- Set YARA version as build argument
    `--build-arg YARA_VERSION=4.5.2`
- Set Go version as build argument
    `--build-arg ARG GO_VERSION=1.23.4`
- Set the Go architecture
    `--build-arg ARG GO_ARCH=linux-arm64`
```
Docker will seeking yara-$YARA_VERSION.zip in the same directory.

## How to run

### Dockerfile.build

```bash
unzip yara-4.5.2.zip
docker run --rm -v -v $(pwd)/yara-4.5.2:/source -v $(pwd)/output:/output yara-builder
```

### Dockerfile.run

```bash
docker run --rm [-v /path_on_host:/scan_path] yara-run -h
```
### Dockerfile.godev
```bash
docker run -dt -v /src_path_on_host:/workdir yara-dev
```