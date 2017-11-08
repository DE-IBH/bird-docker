# BIRD Internet Routing Daemon Check

The images contains agent plugins for [Check_MK](https://mathias-kettner.de/check_mk.html).
The plugin script are based on the [bird-2.1 package](https://mathias-kettner.de/check_mk_exchange.php?_search=bird)
and have been patched to query BIRD IPv4 xor BIRD IPv6. The upstream version tries to query both daemons which won't work
if the run in different containers.


## Usage

Create agent plugin scripts:
- `/usr/lib/check_mk_agent/plugins/bird4`

```
#!/bin/sh

docker exec -it bird_bird4_1 check_bird
```

- `/usr/lib/check_mk_agent/plugins/bird6`

```
#!/bin/sh

docker exec -it bird_bird6_1 check_bird
```
