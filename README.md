# docker-serviio

[![](http://serviio.org/images/serviio.png)](http://serviio.org/) 

[![](https://images.microbadger.com/badges/image/soerentsch/serviio.svg)](https://microbadger.com/images/soerentsch/serviio) [![Docker Pulls](https://img.shields.io/docker/pulls/soerentsch/serviio)](https://hub.docker.com/r/soerentsch/serviio/) [![Docker Stars](https://img.shields.io/docker/stars/soerentsch/serviio)](https://hub.docker.com/r/soerentsch/serviio/) [![GitHub last commit](https://img.shields.io/github/last-commit/soerentsch/docker-serviio/dockerhub.svg)](https://github.com/soerentsch/docker-serviio/dockerhub) [![Join the chat at https://gitter.im/docker-serviio/community](https://badges.gitter.im/docker-serviio/community.svg)](https://gitter.im/docker-serviio/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) 
  
Link on docker hub: [soerentsch/serviio](https://hub.docker.com/r/soerentsch/serviio/)

Link on github: [soerentsch/docker-serviio](https://github.com/soerentsch/docker-serviio)

Started as a fork of [riftbit/docker-serviio](https://github.com/riftbit/docker-serviio), just to provide the newest security and performance patches.

## Usage
```
docker create --name=serviio \
-v /etc/localtime:/etc/localtime:ro \
-v <path to media>:/media \
--net host \
-p 1900:1900/udp \
-p 8895:8895/tcp \
-p 23423:23423/tcp \
soerentsch/serviio:latest
```

The webui is at `<your-ip>:23423/console`.

Serviio serve DLNA over the default port `1900` with `UDP`, the media itself will be provided over port `8895` with `TCP`.

## Container Settings
### Build Args

 - `ALPINE_VERSION` = 3.19.1
 - `SERVIIO_VERSION` = 2.3
 - `JRE_PACKAGE` = openjdk8-jre

### Exposed Ports

 - `1900:1900/udp` - DLNA (Attention! DLNA use UDP!)
 - `8895:8895/tcp` - Serviio Content Delivery
 - `23423:23423/tcp` - HTTP/1.1 /console /rest
 - `23424:23424/tcp` - HTTP/1.1 /cds /mediabrowser

#### Optional SSL Ports (see the Serviio manual)
 - `23523:23523/tcp` - HTTPS/1.1 /console /rest
 - `23524:23524/tcp` - HTTPS/1.1 /cds /mediabrowser

### Recomended Volumes (no auto mounting now)
 - `/opt/serviio/config`
 - `/opt/serviio/library`
 - `/opt/serviio/plugins`
 - `/opt/serviio/log`
 - `/media/serviio` - put media content here and add in serviio gui this path

## Platform differences
### JVM
 - 32bit Platforms (x86, 386, arm7) will use OpenJDK 8 (the latest OpenJDK with 32bit support).
 - 64bit Platforms (x86_64, amd64, aarch64, arm64, s390x) will use OpenJDK 17.

## Container Changelog (dd.mm.yy)
 | Date | Changes |
 | ---- | ------- |
 | **02.02.2024** | Update alpine to 3.19.1. Added ppc64le support.
 | **19.01.2024** | Update FFmpeg to 6.1. Many minor alpine updates.
 | **12.12.2023** | Update alpine to 3.19.0
 | **04.12.2023** | Update alpine to 3.18.5
 | **20.11.2023** | Update FFmpeg to 6.0.1. Many minor alpine updates.
 | **29.09.2023** | Update alpine to 3.18.4
 | **11.08.2023** | Update alpine to 3.18.3
 | **07.07.2023** | Update alpine to 3.18.2
 | **11.05.2023** | Update alpine to 3.18.0
 | **09.05.2023** | Switch back from own build to Alpine package for Jasper 4.0.0
 | **31.03.2023** | Update alpine to 3.17.3
 | **06.03.2023** | Update FFmpeg to 6.0. Many minor alpine updates.
 | **16.02.2023** | Update alpine to 3.17.2
 | **24.01.2023** | Update alpine to 3.17.1
 | **05.01.2023** | Update Jasper to 4.0.0.
 | **08.12.2022** | Added s390x support. Many minor alpine updates.
 | **23.11.2022** | Update alpine to 3.17.0
 | **16.11.2022** | Update alpine to 3.16.3
 | **27.10.2022** | Downgrade OpenJDK from 17 to 8 regarding of an i18n issue of Serviio 2.3.
 | **23.10.2022** | Update Serviio to 2.3.
 | **23.10.2022** | Update OpenJDK to 17.0.5_p8. Many minor alpine updates.
 | **29.09.2022** | Update FFmpeg to 5.1.2. Many minor alpine updates.
 | **06.09.2022** | Update FFmpeg to 5.1.1. Many minor alpine updates.
 | **15.08.2022** | Update alpine to 3.16.2. Replaced librtmp by native FFmpeg routines. Replaced own FFmpeg and Jasper builds by alpine packages, they are up to date and in a good shape. |
 | **22.07.2022** | Update FFmpeg to 5.1
 | **19.07.2022** | Disable the Healthcheck to prevent continuous Disk Activity (#29). Update alpine to 3.16.1, Jasper to 3.0.6. 
 | **12.07.2022** | Added missing dependencies for dcraw and FFmpeg.
 | **24.06.2022** | Update Jasper to 3.0.5. Added JRE_PACKAGE build-arg for MultiArch Support (Hello Raspi ;-))
 | **08.06.2022** | Update Jasper to 3.0.4
 | **03.06.2022** | Added ARG variable for the alpine version
 | **01.06.2022** | Update alpine to 3.16
 | **23.05.2022** | Update FFmpeg to 5.0.1
 | **04.05.2022** | Upgrade OpenJDK from 8 to 17
 | **14.04.2022** | Added alpine edge repository for a newer OpenJDK-JRE version
 | **12.04.2022** | Update alpine to 3.15.4
 | **16.03.2022** | Update Jasper to 3.0.3
 | **16.02.2022** | Update Jasper to 3.0.2
 | **14.02.2022** | Update Jasper to 3.0.1
 | **09.02.2022** | Update Jasper to 3.0.0
 | **24.01.2022** | Update FFmpeg to 5.0
 | **18.12.2021** | Update dcraw
 | **17.12.2021** | Update alpine to 3.15, FFmpeg to 4.4.1, Jasper to 2.0.33
 | **16.12.2021** | Update Serviio version to 2.2.1 (fixed CVE-2021-44228 vulnerability caused by Log4j library)
 | **01.10.2021** | Update Serviio version to 2.2
 | **19.03.2021** | Update FFmpeg to 4.3.2, add healthcheck (PR #19), cleanup volumes (mount only if you need it)
 | **07.12.2020** | Update alpine to 3.12, fix dcraw.c build (add jasper build from source), removed config volume
 | **28.05.2020** | Update Serviio version to 2.1, alpine to 3.11, ffmpeg to 4.2, fix dcraw.c path
 | **27.05.2019** | Update Serviio version to 2.0 and alpine to latest on build date
 | **19.12.2018** | Update Serviio version to 1.10.1 and ffmpeg to 4.1 and alpine to latest on build date
 | **09.05.2018** | Update Serviio version from 1.9.1 to 1.9.2
 | **02.03.2018** | Update Serviio version from 1.9 to 1.9.1
 | **12.01.2018** | dcraw now supported. dockerfile cleanups. many fixes and updates
