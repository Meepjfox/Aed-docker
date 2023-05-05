# AED-Docker #

## Avida-ED, Anti-Bit Rot Edition

## Introduction

Avida-ED is a substantially large software project, and  one of the
issues with continued use of a static software package as a web app
is that the rest of the components may have changes in their
composition: user browsers update, underlying libraries change
interfaces, etc.

In order to provide a means of running Avida-ED as a web app through at
least the medium term (say, ten years or so), we are providing this
project to encapsulate Avida-ED into a Docker container project.
By doing so, we hope to preclude breakage due to ordinary causes
like encountering an incompatible browser update. Because Docker is popular
and programs running in Docker containers should continue to work as
long as backward-compatility continues.

The downside is that Docker containers are more complex to manage
than native executables.

## Rationale (as worded by ChatGPT)

The encapsulation of Avida-ED in a Docker container image offers several advantages that can improve the overall experience for both educators and students working with the web application.

Firstly, a Docker container provides a consistent and reproducible environment, ensuring that Avida-ED runs seamlessly across various systems and platforms. With the container image, educators and students can access the application on their devices without worrying about compatibility issues or environment configurations. This uniformity helps reduce the time spent troubleshooting software-related issues, allowing users to focus on understanding and applying concepts in evolutionary biology and ecology.

Secondly, the standalone server and browser included in the Docker container make it easy to deploy and scale Avida-ED. Educators can quickly set up instances of the application for their students or even use a single instance for a group of students working collaboratively. This ease of deployment reduces the need for dedicated hardware or extensive IT support and simplifies the overall process for both teachers and students.

Thirdly, the encapsulation of Avida-ED in a Docker container improves security by isolating the application from the host system. Containers are self-contained environments, which means any potential vulnerabilities or issues are restricted to the container itself, minimizing the risk to users' devices. This is especially important when working with software in an educational setting, where a diverse range of devices may be used by students.

Lastly, using Docker containers makes it easy to keep Avida-ED up to date. The container image can be readily updated with the latest version of the application, ensuring that educators and students have access to the most recent features and improvements. This streamlined update process not only enhances the user experience but also encourages the adoption of best practices and the latest advancements in evolutionary biology and ecology education.

In conclusion, encapsulating Avida-ED in a Docker container image offers several benefits, including a consistent environment, ease of deployment and scaling, enhanced security, and simplified updates. These advantages make the application more accessible and user-friendly, ultimately promoting a better understanding of complex concepts in evolutionary biology and ecology for college and high school students.

## Prerequisites

### Install Docker

For Windows and Macos, the Docker Desktop is recommended. (Commercial users
will need to obtain a license from Docker, though.)

On Linux, Docker Community Edition should be installed by the user.


## Prerequisites

You will need Docker or Doccker Desktop installed.

You will need the Git version control program installed on your machine.


## Teacher or Student Installation

### Manual Step-wise Instructions

The main thing for the end-user to do is to use the provided images.
Those are intended to be kept in a known-good state. Building using the
development instructions could introduce incompatibilities as newer
software might be installed for dependencies.

The images need to be downloaded, loaded into Docker, re-tagged, and
then invoked. That process goes like this:

Clone this repository.

>  git clone https://github.com/welsberr/aed-docker.git

Enter the local repository directory.

>  cd aed-docker

Enter the images directory.

> cd images

Download the images. (The images exceed the github file size limit of 100MB.)

> wget https://avida-ed-mirror1.beacon-center.org/aed-docker/images/aed_server_image.tar.gz

> wget https://avida-ed-mirror1.beacon-center.org/aed-docker/images/lesage_firefox_image.tar.gz

Load the Avida-ED server container image into your Docker.

>  docker load --input images/aed_server_image.tar.gz

Tag the Avida-ED server container image.

>  docker tag dd96a0629c78 aed-docker_avidaed_server:latest

Load the JLesage/Firefox browser container image into your Docker.

>  docker load --input images/lesage_firefox_image.tar.gz

Tag the JLesage/Firefox browser container image.

>  docker tag 8fafc876063e jlesage/firefox:latest

Bring the two images up in Docker as specified in the Docker Compose file.

>  docker-compose up -d

Docker should show the following:

>  Starting avidaed_server ... done

>  Starting avidaed_browser ... done

In a browser, enter this URL:

>  localhost:5800

The Avida-ED Eco instance should be launched in that browser window, and can be
used there.



### Python program guided installation

TBD



## Development Installation

### Prerequisites


Clone the 'aed-docker' repository.

> git clone https://github.com/welsberr/aed-docker.git

> cd aed-docker

### Docker Compose step

The two images get built and run using Docker Compose.

> docker-compose up -d

The first time this runs, it will take time to download necessary
files and set up the Avida-ED source files and libraries.

### Accessing Avida-ED

In a browser, enter this URL:

> localhost:5800

That will display a new Firefox browser page that is running in your
browser.

Within that page, enter this URL:

> avidaed_server:80/Avida-ED-Eco/index.html


That should bring up Avida-ED in the Firefox page.

Do whatever work is necessary. Commit changes to Github. Remove the
Docker container associated with aed-server.

> docker images

Examine the list, and recognize the aed-server Docker container
ID. Use that container ID to remove it.

> docker rmi -f <container ID>

Run the docker-compose command.

> docker-compose up -d

That will generate a new version of the aed-server image.

The aed-server image needs to be exported from Docker.

> docker save <new image id>  > images/aed_server_image.tar

Gzip it to reduce the size.

> gzip images/aed_server_image.tar

Update the project README.md with the <new image id> for the aed_server image.
This is especially needed for the 'docker tag' command for the aed_server image.

Commit all changes to git.

> git commit -m "<My commit comment goes here>"

Push local changes to Github.

> git push


