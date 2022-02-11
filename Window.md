#Run GUI app in linux docker container on windows host
https://dev.to/darksmile92/run-gui-app-in-linux-docker-container-on-windows-host-4kde

docker run -it -e DISPLAY=host.docker.internal:0.0 debian:buster