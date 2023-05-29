# More About Running Containers

- ```docker run -d -p 80 --restart always nginx```: Should the container start, or the Docker host itself restart, the container will restart so that it has a high uptime. But it actually works too well; if you try to stop the container using the docker stop command, it will not stop.
- If you want your container to always be running except when you explicitly stop it, use the unless_stopped restart mode: ```docker run -d -p 80 --restart unless-stopped nginx```. <br>
  That way, your container will almost always be up, except when you don’t want it to.
- ```docker stats```: This will output a live list of running containers plus information about how many resources they consume on the host machine. Like a ```docker ps``` extended with live resource usage data.
- Dangling images: images that have no name. This happens when you docker build an image with the same tag as before, the new one replaces it and the old one becomes dangling.
- Most commands ask for an interactive confirmation, but if you want to run them unattended you can add the -f switch.
- Here are the commands you can run to remove the items that you don’t need:
  ```
  docker container prune -f
  docker volume prune -f
  docker image prune -f
  ```
- If you want to remove all unused images, just use the following command: ```docker image prune --all```.
- In a rolling update, a new container is started with the newest image, and once it is ready, users are routed to it, then the old container is removed.
