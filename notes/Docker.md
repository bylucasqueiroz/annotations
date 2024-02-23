
Start Docker

```bash
sudo service docker start
```

Check container logs

``` bash
docker logs <container_name>
```

Delete docker container

``` bash
docker rm -f <container_id_or_name>
```
## Docker Compose

Start docker compose without container logs

``` bash
docker-compose up -d
```

Recreating Containers

``` bash
docker-compose up --force-recreate -d
```

Clean docker after remove an image

``` bash
docker-compose up -d --remove-orphans
```