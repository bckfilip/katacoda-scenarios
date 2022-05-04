Docker is a tool that allows the packaging of an application, with its dependencies, into a standardized environment for software development. The application is deployed in a container, sometimes called a sandbox, which enables it to be run on the hosts OS.

The wiki definition:

>an open-source project that automates the deployment of software applications inside containers by <
>providing an additional layer of abstraction and automation of OS-level virtualization on Linux.

The strength of deploying an application via a container compared to a VM is that it is lightweight - it provides most of the same isolation as a VM but at a fraction of the cost.

The container allows for an abstraction from the environment the application is run in, making for an easy deployment regardless of the target environment. 


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