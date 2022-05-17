# Docker CLI

The interactive terminal to the right is launched with ubuntu, enabling us to use Docker from the terminal. The Docker CLI allows us to run Docker commands from the terminal without need need for a DockerHub account or similar.

# Createing a docker image

As the Dockerfiles are in place from the previous section, we can use the `build` command to build our image. We are attaching a flag to the command, `-t` , which allows us to tag the image making it easier for us to identfy it.

`docker build . -t app`{{execute}}

If we then run the following command we can see our listed image

`docker images`{{execute}}

This command will list the active images in the terminal.

Now that we can see our built image is listed, we can run a container from it with

`docker run -p 49160:8080 -d app`{{execute}}

The `-d` flag allows us to run the container in a detached mode, allowing it to run in the background. The `-p` flag redirects a public port to a private one inside the container. This means that Docker mapped the `8080` port inside the container to the `49160` port on your local machine.

If we then run the

`docker ps`{{execute}}

command we can see our container listed in the terminal.

Finally, we can call our application using the `curl` command to retrieve info about or application to the terminal.

`curl -i localhost:49160`{{execute}}

And this will then show the information about or application in the terminal.
