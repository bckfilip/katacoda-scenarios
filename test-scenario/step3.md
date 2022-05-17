# Creating a docker image?

Docker is a tool that allows the packaging of an application, with its dependencies, into a standardized environment for software development. The application is deployed in a container, sometimes called a sandbox, which enables it to be run on the hosts OS.

The wiki definition:

> an open-source project that automates the deployment of software applications inside containers by
> providing an additional layer of abstraction and automation of OS-level virtualization on Linux.

The strength of deploying an application via a container compared to a VM is that it is lightweight - it provides most of the same isolation as a VM but at a fraction of the cost.

The container allows for an abstraction from the environment the application is run in, making for an easy deployment regardless of the target environment.

In this section, we will use a lot of Docker-specific terms which might be confusing to some. So let's clarify some terminology that is used before we dive in.

Images - The blueprints of our application which form the basis of containers.

Containers - Created from Docker images and run the actual application. We create a container using 'docker run'. A list of running containers can be seen using the 'docker ps' command.

Docker Daemon - The background service running on the host that manages building, running and distributing Docker containers. The daemon is the process that runs in the operating system which clients talk to.

# commands:

'docker images' - lists all images on your system.

'docker run' - the Docker client finds the specified image, loads up the container and then runs a command in that container. (flag -it attaches an interactive terminal allowing the use of additional commands to be run in a container)

'docker ps' - lists all currently running containers (flag -a show previously ran containers)

'docker rm' - removes containers by specifying their ID

'docker stop' - stops a detached container

'docker exec' - runs a command inside an active container

# Moving on to the files..

In order to deploy our server with docker we first need to create a Dockerfile:

`touch Dockerfile`{{execute}}

This Dockerfile can be seen as a configuration file for our Docker setup. The file will contain 6 different commands:

- FROM : Specifies the base image. An image in Docker can be seen as the blueprint of the application which forms the bases of a container.
- WORKDIR : Sets the working directory for the application.
- COPY : Copies existing files to the image at run-time.
- RUN : Runs a command in a container. Allows for the override / addition of the image defaults.
- EXPOSE : Specifies the network port(s) the container should listen to at runtime.
- CMD : Provides defaults for an executing container.

Adding these commands to our Dockerfile would then look like

<pre class="file" data-target="clipboard">

FROM node:16

# Working directory
WORKDIR /usr/src/app

# Install app dependencies
COPY package*.json ./

# Installs dependencies within the container
RUN npm install

# Bundles the source code inside the Docker image
COPY . .

# Sets network port
EXPOSE 8080

# Define executables
CMD [ "node", "app.js" ]

</pre>

In addition to this, we are going to add a .dockerignore file which ignores the copying of local modules and debug files

`touch .dockerignore`

<pre class="file" data-target="clipboard">
node_modules
npm-debug.log
</pre>

While a .ignore file is good practice it won't be necesary in this specific tutorial.

Now that the Dockerfile is in place, we can head over the next section which will show how to dockerize the application.

### Links

If you are interested in reading more about Docker commands please visit [Docker Desktop](https://docs.docker.com/desktop/).
