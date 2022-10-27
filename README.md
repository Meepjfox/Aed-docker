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

## Prerequisites

### Install Docker

For Windows and Macos, the Docker Desktop is recommended. (Commercial users
will need to obtain a license from Docker, though.)

On Linux, Docker Community Edition should be installed by the user.


## Installation

### Manual Step-wise Instructions

Clone the project from Github.




### Python program guided installation

TBD

## Building

### Prerequisites

You will need Docker or Doccker Desktop installed.

You will need the Git version control program installed on your machine.

Then clone the 'aed-docker' repository.

> git clone https://github.com/welsberr/aed-docker.git
> cd aed-docker

### Docker Compose step

The two images get built and run using Docker Compose.

> docker-compose up -d

The first time this runs, it will take time to download necessary
files and set up the Avida-ED source files and libraries.

### Accessing Avida-ED

In a browser, enter this URL:

> 0.0.0.0:5800

That will display a new Firefox browser page that is running in your
browser.

Within that page, enter this URL:

> avidaed_server:80/Avida-ED-Eco/index.html


That should bring up Avida-ED in the Firefox page.





