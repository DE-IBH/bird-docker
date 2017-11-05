# The BIRD Internet Routing Daemon

These are docker images for [bird](http://bird.network.cz/) based on the offical Debian package:
- **liske/bird** - IPv4 version of bird
- **liske/bird6** - IPv6 version of bird


## Tagged Docker Images

Images are tagged according to the installed bird version. The images are based on official Debain GNU/Linux releases.

* [`1.6.3`, `latest` Dockerfile](https://github.com/liske/bird-docker/blob/master/bird-1.6.3-debian/Dockerfile)

  [![Layers](https://images.microbadger.com/badges/image/liske/bird:1.6.3.svg)](https://images.microbadger.com/badges/image/liske/bird:1.6.3)
  This image is build using *Debian stretch* and should be considered **stable** (*recommended*).


## Usage

```
$ docker run --rm --net=host --uts=host --cap-add=NET_ADMIN --cap-add=NET_BROADCAST --cap-add=NET_RAW -v /path/to/config:/etc/bird:ro liske/bird
```

The command is used as options for bird (which is already the entrypoint).

```
# docker-compose.yml example
version: '3'
services:
  bird:
    image: liske/bird
    cap_add:
      - NET_ADMIN
      - NET_BROADCAST
      - NET_RAW
    network_mode: host
    volumes:
      - /path/to/config:/etc/bird:ro

  bird6:
    image: liske/bird6
    cap_add:
      - NET_ADMIN
      - NET_BROADCAST
      - NET_RAW
    network_mode: host
    volumes:
      - /path/to/config:/etc/bird:ro
```
