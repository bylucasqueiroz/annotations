### Commands
___
#### Start Docker

```bash
sudo service docker start
```
#### Stop Docker

```bash
sudo service docker stop
```
#### Check container logs

``` bash
docker logs (container_name)
```
#### Delete docker container

``` bash
docker rm -f (container_id_or_name)
```
#### Stop all containers

```bash
docker stop $(docker ps -a -q)
```
#### Remove all containers

```bash
docker rm $(docker ps -a -q)
```
### Docker Compose
___
#### Start docker compose without container logs

``` bash
docker-compose up -d
```
#### Recreating Containers

``` bash
docker-compose up --force-recreate -d
```
#### Clean docker after remove an image

``` bash
docker-compose up -d --remove-orphans
```