# docker-icecream
Dockerized images of icecream distributed compiler with their docker-compose files

## Usage
### Daemon
The daemon images is based on Clearlinux so as to enjoy performance out of the optimized distribution
```
docker run --net=host -p ::10245 -p ::8766 -p ::8765 adambh/docker-iceccd
```

### Scheduler
There are 2 flavors of this image, in Clearlinux and in Alpine, the former favors performance and the latter size.

#### Clearlinux
```
docker run --net=host -p ::8765 adambh/docker-icecc-scheduler:latest
```

#### Alpine
```
docker run --net=host -p ::8765 adambh/docker-icecc-scheduler:alpine
```

