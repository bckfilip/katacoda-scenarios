Docker is a tool that allows the packaging of an application, with its dependencies, into a standardized environment for software development. The application is deployed in a container, sometimes called a sandbox, which enables it to be run on the hosts OS.

The wiki definition:

>an open-source project that automates the deployment of software applications inside containers by
providing an additional layer of abstraction and automation of OS-level virtualization on Linux.

The strength of deploying an application via a container compared to a VM is that it is lightweight - it provides most of the same isolation as a VM but at a fraction of the cost.

The container allows for an abstraction from the environment the application is run in, making for an easy deployment regardless of the target environment. 


In order to deploy our server with docker we first need to create an file called Dockerfile:

`touch Dockerfile`{{execute}}

This Dockerfile can be seen as a configuration file for our Docker setup. The file will contain 6 different commands:
- FROM : Specifies the base image. An image in Docker can be seen as the blueprint of the application which forms the bases of a container.
- WORKDIR : Sets the working directory for the application.
- COPY : Copies existing files to the working directory.
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

`touch .dockerignore`{{execute}}

<pre class="file" data-target="clipboard">
node_modules
npm-debug.log
</pre>

Now that the Dockerfiles are in place we can use the `build` command to build our image. We are attaching a flag to the command, `-t` , which allows us to tag the image making it easier for us to identfy it.

`docker build . -t app`{{execute}}

If we then run the following command we can see our listed image

`docker images`{{execute}}

Now that we can see our built image is listed we can run it. 

`docker run -p 49160:8080 -d app`{{execute}}

The `-d` flag allows us to run the container in a detached mode, allowing it to run in the background. The `-p` flag redirects a public port to a private one inside the container. This means that Docker mapped the `8080` port inside the container to the `49160` port on your local machine.

Finally, we can call our application using the `curl` command to retrieve info about or application to the terminal.

`curl -i localhost:49160`

In the last section, we used a lot of Docker-specific jargon which might be confusing to some. So before we go further, let me clarify some terminology that is used frequently in the Docker ecosystem.

Images - The blueprints of our application which form the basis of containers.

Containers - Created from Docker images and run the actual application. We create a container using 'docker run'. A list of running containers can be seen using the 'docker ps' command.

Docker Daemon - The background service running on the host that manages building, running and distributing Docker containers. The daemon is the process that runs in the operating system which clients talk to.

commands:
'docker images' - lists all images on your system.
'docker run' - the Docker client finds the specified image, loads up the container and then runs a command in that container. (flag -it attaches an interactive terminal allowing the use of additional commands to be run in a container)
'docker ps' - lists all currently running containers (flag -a show previously ran containers)
'docker rm' - removes containers by specifying their ID
'docker stop' - stops a detached container
'docker exec' - runs a command inside an active container