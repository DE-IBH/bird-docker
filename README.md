# The BIRD Internet Routing Daemon

These are docker images for [bird](http://bird.network.cz/) based on the offical Debian package:
- **liske/bird4** - IPv4 version of BIRD
- **liske/bird6** - IPv6 version of BIRD


## Tagged Docker Images

Images are tagged according to the installed BIRD version. The images are based on official Debain GNU/Linux releases.

### bird4

* [`1.6.3`, `latest` Dockerfile](https://github.com/liske/bird-docker/blob/master/bird4-1.6.3-debian/Dockerfile)

  [![Layers](https://images.microbadger.com/badges/image/liske/bird4:1.6.3.svg)](https://images.microbadger.com/badges/image/liske/bird4:1.6.3)
  This image is build using *Debian stretch* and should be considered **stable**.

### bird6

* [`1.6.3`, `latest` Dockerfile](https://github.com/liske/bird-docker/blob/master/bird6-1.6.3-debian/Dockerfile)

  [![Layers](https://images.microbadger.com/badges/image/liske/bird6:1.6.3.svg)](https://images.microbadger.com/badges/image/liske/bird6:1.6.3)
  This image is build using *Debian stretch* and should be considered **stable**.


## Usage

```
$ docker run --rm --net=host --uts=host --cap-add=NET_ADMIN --cap-add=NET_BROADCAST --cap-add=NET_RAW -v /path/to/config:/etc/bird:ro liske/bird4
```

The command is used as options for BIRD (which is already the entrypoint).

```
# docker-compose.yml example
version: '3'
services:
  bird4:
    image: liske/bird4
    cap_add:
      - NET_ADMIN
      - NET_BROADCAST
      - NET_RAW
    network_mode: host
    volumes:
      - /path/to/config4:/etc/bird:ro

  bird6:
    image: liske/bird6
    cap_add:
      - NET_ADMIN
      - NET_BROADCAST
      - NET_RAW
    network_mode: host
    volumes:
      - /path/to/config6:/etc/bird:ro
```

### CLI

To use the CLI from outside you could use two following wrapper scripts. This also allows the usage of the [BIRD Internet Routing Daemon Check](https://github.com/liske/bird-docker/blob/master/Check_MK.md) plugin for Check_MK on the host.


- `/usr/local/bin/birdc`

```
#!/bin/bash

if [ -t 0 ]; then
    exec docker exec -it bird_bird4_1 birdc $@
else
    exec docker exec -i bird_bird4_1 birdc $@
fi
```

- `/usr/local/bin/birdc6`

```
#!/bin/bash

if [ -t 0 ]; then
    exec docker exec -it bird_bird6_1 birdc6 $@
else
    exec docker exec -i bird_bird6_1 birdc6 $@
fi
```
