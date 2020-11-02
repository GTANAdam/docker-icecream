# docker-icecream
Dockerized images of icecream distributed compiler with their docker-compose files

## Usage
### Daemon ([adambh/docker-iceccd](https://hub.docker.com/r/adambh/docker-iceccd))
The daemon images is based on Clearlinux so as to enjoy performance out of the optimized distribution
```
docker run --net=host -p ::10245 -p ::8766 -p ::8765 adambh/docker-iceccd
```

### Scheduler ([adambh/docker-icecc-scheduler](https://hub.docker.com/r/adambh/docker-icecc-scheduler))
There are 2 flavors of this image, in Clearlinux and in Alpine, the former favors performance and the latter size.

#### - Clearlinux
```
docker run --net=host -p ::8765 adambh/docker-icecc-scheduler:latest
```

#### - Alpine
```
docker run --net=host -p ::8765 adambh/docker-icecc-scheduler:alpine
```

## Troubleshooting
### Scheduler is not automatically reachable when running a daemon on Windows:
This is a known [limitation](https://docs.docker.com/docker-for-windows/networking/#known-limitations-use-cases-and-workarounds) of Docker on Windows, but this can be workedaround by manually setting the IP Address of the scheduler via environment variables, for example:

**Note**: Replace 192.168.1.12 with your scheduler's IP address.

```
docker run --net=host -p ::10245 -p ::8766 -p ::8765 -e USE_SCHEDULER=192.168.1.12 adambh/docker-iceccd
```

or by appending environment variable to **docker-compose.yml**:

```
environment:
  - USE_SCHEDULER=192.168.1.12 # Replace with the scheduler's IP address
```

### I've done the prior workaround but I am still getting `` failed to accept an incoming connection on [MY IP]:10245``
Yeah well, the prior workaround was half of the solution, it is rather better to create a VPN between the scheduler and the daemon then bridge it to the same docker network.
