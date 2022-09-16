# AED-Docker #

Simple project to serve Avida-ED-Eco via NGINX.

Eventually, we want to incorporate a fixed browser executable into this
so that all software resides in a container project.



## From the email describing the demo: ##



Build NGINX container:

docker build .

Run server:

docker run -it --rm -d -p 8080:80 --name web  e1fbf99f9558

(The container name is a default provided by Docker.)

Invoking Docker Firefox:

docker run -d     --name=firefox     -p 5800:5800     -v /docker/appdata/firefox:/config:rw     --shm-size 2g     jlesage/firefox

## From a later email to Jimin Song: ##

One way I've thought of to do development and test with the container setup would be to use a bind volume with the NGINX container in dev. That way, the Avida-ED source files can be in the local filesystem, but be served by the NGINX container. This would mean that dev and production would have slightly different Dockerfiles, but it is about the easiest approach I am thinking of to handle this.

If you have another approach in mind, please let me know.


Summarizing what I recall from yesterday's meeting:

Highest priority is to produce a Docker-based Avida-ED system that serves Avida-ED 4 and includes a fixed-build browser to run the application. Documentation sufficient to allow a casual user to set up Docker, run the Docker image, and launch the application will be needed. This will serve to fulfill the goals of the supplemental grant, and needs to be done by mid-October.

Beyond that, we will be looking for user experience improvements to reduce the technical burden for use. This may include further work on Docker containers, but also may involve other approaches to be identified. We discussed the possibility of use of Cosmopolitan/RedBean in this way.




