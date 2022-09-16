# AED-Docker #

Simple project to serve Avida-ED-Eco via NGINX.

Eventually, we want to incorporate a fixed browser executable into this
so that all software resides in a container project.



From the email describing the demo:



Build NGINX container:

docker build .

Run server:

docker run -it --rm -d -p 8080:80 --name web  e1fbf99f9558

(The container name is a default provided by Docker.)

Invoking Docker Firefox:

docker run -d     --name=firefox     -p 5800:5800     -v /docker/appdata/firefox:/config:rw     --shm-size 2g     jlesage/firefox



