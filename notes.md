# Instructor Notes

We are going to cover a lot of ground during class. These notes are to help keep
me on track, and to give you something you can refer to following class.

## Running Docker

```
docker run hello-world
docker pull alpine
docker run alpine echo "hello from alpine"
docker run alpine /bin/sh
docker run -it alpine /bin/sh
/ # ls
/ # uname -a
/ # exit
```

## Docker Containers

```
docker ps -a
docker rm <container id>
docker rm <container name>
docker ps -a
docker ps -aq
docker rm `docker ps -aq`
```

## Docker Ports and Volumes

```
docker run --rm -it nginx
docker run --rm -it -p 8080:80 nginx
docker run --rm -it -p 8080:80 -v $(pwd)/example-website:/usr/share/nginx/html nginx
docker run -d -P -v $(pwd)/example-website:/usr/share/nginx/html nginx
docker ps
docker logs -f <container name>
docker rm -f <container name>
```

## Docker Images

```
docker images
docker rmi hello-world
docker images
docker pull node
docker pull node:onbuild
docker images
docker search node
```

## Custom Images

```
docker build -t example-api example-api
docker run -d -p 3000:3000 example-api
curl -X GET http://localhost:3000/heroes
curl -H "Content-Type: application/json" -X POST \
  -d '{"id":3,"name":"Robin","secret_identity":"Dick Grayson"}' \
  "http://localhost:3000/heroes"
curl -X GET http://localhost:3000/heroes
```

## Exercise 1

Use your Docker skills to run the spring-boot app.

## Linking Containers

```
docker build -t httpie httpie
docker run --rm -it httpie get localhost:3000/heroes
docker run --rm -it --link <container name>:example httpie get example:3000/heroes
docker run --rm -it --network host httpie get localhost:3000/heroes
alias httpie="docker run --rm -it --network host httpie"
httpie post localhost:3000/heroes name=Hulk secret_identity="Bruce Banner"
httpie get localhost:3000/heroes
docker rm -f <container name>
docker run -d --name example example-api
docker run --rm --link example httpie get example:3000/heroes
```

## Running Docker Compose and Named Volumes

```
cd wordpress
docker-compose up
# setup wordpress
docker-compose down
docker-compose up -d
docker-compose logs -f
docker-compose down
docker volumes ls
docker volumes rm wordpress_db_data
docker-compose up
```

## Exercise 2

Follow the [Compose and Rails Quickstart](https://docs.docker.com/compose/rails/)
to create a Rails app with PostgreSQL.
