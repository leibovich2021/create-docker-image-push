# create-docker-image-push
How create docker file(image) and push to dockerhub

1. create PHP file (name file is index.php)

2.create Dockerfile with apache+PHP+us file (name file is Dockerfile)

3.create docker image from us Dockerfile (create local image)
$ docker build -t (name) (name file)
For example: docker build -t denis2022 . 
(I put a period because I want to work with all the files I have in the folder)
now for check if this work :
$ docker images
and us output need be: 
REPOSITORY                     TAG       IMAGE ID       CREATED         SIZE
denis2022                      latest    9521a6a56839   8 minutes ago   1.18GB

4. make Repository in DokerHub
now we create us tag and push to repository
docker tag REPOSITORY:TAG (us name repository in dockerhub)REPOSITORY:TAG
For example : docker tag denis2022:latest leibovich2021/docker-image-push:latest
and now we check if this work
$ docker images
output need to be like this:
REPOSITORY                        TAG       IMAGE ID       CREATED          SIZE
leibovich2021/docker-image-push   latest    9521a6a56839   27 minutes ago   1.18GB
denis2022                         latest    9521a6a56839   27 minutes ago   1.18GB


5.upload us Doker image in us Repository on DokerHub
now we connect to us docker hub
$ docker login
and push our image
$ docker push (name of repository)
for exmaple : docker push leibovich2021/docker-image-push:latest

6. make a test of download us docker image from us DockerHub 
for this we need to delete the image from us computer local
$ docker images
and take name of REPOSITORY
$ docker rmi (name of REPOSITORY)
example : docker rmi leibovich2021/docker-image-push
and now finly we run us image from docker hub
$ docker run (-it or -d) -p (select port:80) (name for repository)

for example : docker run -it -p 1234:80 leibovich2021/docker-image-push

link to my dockerhub : https://hub.docker.com/repository/docker/leibovich2021/docker-image-push
