# yara with docker

This is a Project to help you compile and run Yara as soon as possible.

## How to build

```bash
docker build -f Dockerfile.build -t yara-builder .
docker build -f Dockerfile.run --build-arg YARA_VERSION=4.5.2 -t yara-run .
```

## How to run

### Dockerfile.compile

```bash
unzip yara-4.5.2.zip
docker run --rm -v -v $(pwd)/yara-4.5.2:/source -v $(pwd)/output:/output yara-builder
```

### Dockerfile.run

```bash
docker run --rm [-v /path_on_host:/scan_path] yara-run -h
```