# Dremio Docker Build with Dezota Extensions (Thin)

This docker build is different from the standard Dremio OSS build in the
following ways:

1. Patched Dremio OSS to support longer Varchar and VarBinary fields (needed
to support GIS geometry length).  Keep in mind that these values only define 
an absolute maximum but will not inflate the size smaller values.

   - Moved default size to 10,485,759 bytes from 31,999 bytes
   - Moved maximum size to 10,485,759 bytes from 65,536 bytes 

2. Incorporate support for ClickHouse as a Datasource from:

   - https://github.com/Dezota/dremio-clickhouse-connector

3. Incorporate GIS functionality including GIS function search in *Dremio Analyst
Center* UI

   - https://github.com/Dezota/dremio-gis-extensions

# Why Thin?

This docker build doesn't do the actual compiling of the patched Dremio or
the two extensions  unlike this
[build](https://github.com/Dezota/dremio-docker-with-extensions).  It takes
a complete RPM package from the other docker build and installs it in a
small *RedHat Universal Binary Image 8* leading to a 40% smaller image.

## Building and Running Docker Image

```
cd ./build
make build
make run
```

## Using the Docker Hub Image

![About Dremio with Dezota Extensions](./about_dremio_ext.jpg)

Get the image from Docker HUB:
```
docker pull dezota/dremio-oss-with-ext-thin:22.0.0-1
```

Here is the digest for the this version on hub.docker.com:
```
22.0.0-1: digest: sha256:c309b63dc838c794db9b35189386f994e87eec64f2355f7edfe0f9c1e5d0b300 size: 1578
````

*Comment out build line in docker-compose.yml:*
```
# build: ./build
```

Launch Dremio with Dezota Extensions in the Background:
```
docker-compose up -d
```
