# list all docker images

function listimages() {
sudo docker images
}

# run docker with GUI enabled

# usage: runimage imagename:tag --name=Test

# eg: runimage debian10:RVS --name=RVSTest

function runimage() {
xhost +
sudo docker run -it -p 5180:5180 -e "DISPLAY=unix:0.0" -v="/tmp/.X11-unix:/tmp/.X11-unix:rw" --privileged --net=host $2 $3 "\$1" bash
}

# eg: commitimage 493a debian10:RVS_NEW

function commitimage() { # $1: container id, $2 new_image_name:tag_name
sudo docker commit $1 $2
}

# list all containers

function listcontainers() {
sudo docker container ls -a
}

# attach a running container

function attachcontainer() {
sudo docker exec -it "\$1" bash
}

# start a container

function startcontainer() {
xhost +
sudo docker container start \$1
}

# stop a container

function stopcontainer() {
sudo docker container stop \$1
}

# remove a container

function removecontainer() {
sudo docker container rm \$1
}

# export a container to file

# usage: exportcontainer container_hash filename

# eg: exportcontainer cb381a6a6d65 debian10_RVS

function exportcontainer() {
sudo docker export $1 > $2.tar
}



在vscode中使用Docker
1.Manage Docker as a non-root user
```
sudo groupadd docker
sudo usermod -aG docker \$USER
newgrp docker

```


## 上传 image 到docker hub