# docker-icecream
Dockerized images of icecream distributed compiler with their docker-compose files

## Installation
### Daemon
```docker run --net=host -p ::10245 -p ::8766 -p ::8765 adambh/docker-iceccd```

### Scheduler
```docker run --net=host -p ::8765 adambh/docker-icecc-scheduler```
