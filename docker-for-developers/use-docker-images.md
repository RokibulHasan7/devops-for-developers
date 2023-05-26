# Use Docker Images

- ```docker ps```: lists the containers that are still running. Add the -a switch in order to see containers that have stopped.
- ```docker logs```: retrieves the logs of a container, even when it has stopped.
- ```docker inspect```: gets detailed information about a running or stopped container.
- ```docker stop```: stops a container that is still running.
- ```docker rm```: deletes a container.
- You can think of the docker run command as the equivalent of buying a new computer, executing some command on it, then throwing it away. Each time a container is created from an image, 
  you get a new isolated and virgin environment to play with inside that container.
- Docker is a tool that allows you to get the equivalent of a disposable, single-time use computer.
- ```docker container prune -f```: This is the equivalent of running one ```docker rm``` command for each stopped container. The ```-f``` switch is an implicit confirmation to proceed and delete all 
  stopped containers right away, instead of asking to confirm that operation.
- Don’t store information inside the containers.  In other words, ensure your containers are stateless, not stateful. A stateless container never stores its state when it is run while stateful 
  containers store some information about their state each time they are run.
- A server container:
  - is long-lived.
  - listens for incoming network connections.
- To disconnect while allowing the long-lived container to continue running in the background, we use the `````-d or –detach``` switch on the ```docker run``` command.
- Running a container as detached means that you immediately get your command-line back and the standard output from the container is not redirected to your command-line anymore.
- We can get a portion of the output using the ```–from, –until, or –tail``` switches. Let’s see the most recent 10 seconds of logs for our running container: ```docker logs --since 10s <container-id>```.
- In real-world applications with multiple running containers, you would typically redirect your containers’ output to log management services. 
- You must explicitly open a port on the host machine and map it to a port on the container.
- When using such images, you could wonder about where the data is stored. Docker uses volumes for this.
- Running the NGINX web server:
  - It listens for incoming HTTP requests on port 80 by default. If I simply run the server, my machine does not route incoming requests to it unless I use the ```-p``` switch on the docker run command.
  - The -p switch takes two parameters; the incoming port you want to open on the host machine, and the port to which it should be mapped inside the container. For instance, here is how I state that 
    I want my machine to listen for incoming connections on port 8085 and route them to port 80 inside a container that runs NGINX: ```docker run -d -p 8085:80 nginx```.
  - I could also run two separate NGINX servers by just executing the docker run command again using another port.
- When a container writes files, it writes them inside of the container. Which means that when the container dies (the host machine restarts, the container is moved from one node to another in a cluster, it simply fails, etc.) 
  all of that data is lost. It also means that if you run the same container several times in a load-balancing scenario, each container will have its own data, which may result in inconsistent user experience.
- A rule of thumb for the sake of simplicity is to ensure that containers are stateless, for instance, storing their data in an external database (relational like an SQL Server or document-based like MongoDB) 
  or distributed cache (like Redis). However, sometimes you want to store files in a place where they are persisted; this is done using volumes.
- Suppose you run a MySQL database with no volume: ```docker run -d mysql:5.7```. Any data stored in that database will be lost when the container is stopped or restarted. In order to avoid data loss, you can use a volume mount:
  ```docker run -v /your/dir:/var/lib/mysql -d mysql:5.7```. It will ensure that any data written to the /var/lib/mysql directory inside the container is actually written to the /your/dir directory on the host system. 
  This ensures that the data is not lost when the container is restarted.
- A pull command forces an image to download, whether it is already present or not.
- Here are some scenarios where using a docker pull command is relevant:
  - You expect that the machine which runs the containers does not have access to the registries (e.g., no internet connection) at the time of running the containers.
  - You want to ensure you have the latest version of an image tagged as “latest,” which wouldn’t be downloaded by the docker run command.


