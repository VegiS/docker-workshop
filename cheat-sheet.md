## Pulling images

`docker pull ubuntu:14:04`

## Run a container and attach to it:

`docker run -it ubuntu:14:04 bash`

## List containers

`docker ps # List running containers`
`docker ps -a # List all containers`

## Run a container in the background:

`docker run -d --name=redis redis`

## Get inside a running container:

`docker exec -it redis bash`

## Link to an existing container:

`docker run -it --link=redis:redis redis redis-cli -h redis`

## Expose a container port

`docker run -d -p=80 --name=static-nginx nginx`

## Get an exposed port

`docker port static-nginx 80`

## Expose a container port to a specific host port

`docker run -d -p=80:80 static`

## See a container's logs

`docker logs -f flask`

## Directly attach to a container

`docker attach flask`

## Create a network

`docker network create demo`

## Set the network of a container

`docker run -d --net=demo --net-alias=redis redis`

## Dynamically add a container in a network

`docker network connect --alias=redis demo redis`

## Create a volume

`docker create volume myvol`

## Mount a volume to a container

`docker run -v=myvol:/mnt/data ubuntu echo hello > /mnt/data/hey.txt`
`docker run -v=myvol:/mnt/data ubuntu cat /mnt/data/hey.txt`

## Mount all volumes from another container

`docker run --volumes-from=some-container -it ubuntu bash`

## Run a Docker Compose stack

`docker-compose up -d`

## Run another command inside a running container

`docker-compose exec django ./manage.py migrate`
