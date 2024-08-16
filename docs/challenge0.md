### Challenge 0
Objective: 
- Learn how to list, pull, delete images.
- Learn how to run containers, what containers are, how to list them, how to override their default commands



```sh
$ docker container run hello-world
```
[](../assets/image.png)

```sh
$ docker image ls
# You should see a listing of docker images

$ docker image pull alpine 
$ docker image ls
# you should see alpine now listed
# these images can now be used to run containers

$ docker container ls
# This should list any running containers you have. Please note the `running` keyword.

# Let's run some commands
```sh
$ docker container run alpine ls -l
$ docker container run alpine ifconfig
```

This is going create a container based on the alpine image, then execute the `ls -l` command inside that running container. The container will stop directly after execution of `ls -l` stops.  
How do we go into the docker container to interactively? We need two pieces in order to do that. First, the `-it` option when passed to `docker container run` and also the `/bin/sh` or `/bin/bash` at the end of the command. By overriding the default command of the container with the binary executable for the terminal we trick docker into giving us a terminal inside of the container.
```sh
$ docker container run -it alpine /bin/sh
...
$ exit # run this from your container and we're gonna investigate some things about the exited container
```

You should notice by this point that everytime you perform a `docker container run` you will end up with a completely new container. This is because of the nature of `docker container run`, which will effectively perform both a `docker container create` & `docker container start` command. It's just an easier way to do it.

Let's make sure you don't have any containers running still.
```sh
$ docker container run -d alpine sleep 600
$ docker container ls
# Some of the details will be a bit different for you
CONTAINER ID   IMAGE     COMMAND      CREATED          STATUS          PORTS     NAMES
859995aa421b   alpine    "sleep 60"   37 seconds ago   Up 36 seconds             exciting_pare

```

#### Investigate a container
Let's investigate some things about our dead (exited) containers.
First let's find our dead container.
```sh
$ docker container ls
```
You'll notice that you only see running containers, assuming you have any.