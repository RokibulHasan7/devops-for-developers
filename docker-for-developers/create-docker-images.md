# Create Docker Images

- A Docker image is created using the docker build command and a Dockerfile file. 
- The Dockerfile file can have any name. Naming it Dockerfile makes it easier for others to understand its purpose when they see that file in your project.
- A Dockerfile file always begins with a FROM instruction because every image is based on another base image.
- The CMD instruction specifies which executable is run when a container is created using your image and provides optional arguments. Example: ```CMD ["echo", "Hello World"]```.
- In order to create an image from my Dockerfile file, I need to run the docker build command. To do this, I type the following command in my terminal in the folder 
  where the Dockerfile file lives: ```docker build -t hello .```. <br>
- ```docker run hello``` : To run hello docker image.
- ```docker run --rm -it -p 8082:80 webserver```: The ```-it``` switch allows me to stop the container using Ctrl-C from the command-line. The ```–rm``` switch ensures that the container is deleted once it has stopped.
- ```docker rmi <image-name or image-id>```: To remove docker image.
- You can give environmental variable in Dockerfile. Using ```ENV```. Example: ```ENV host=www.google.com```.
- Also you can give it from command line. Example: ```docker run --rm -e host=www.google.com pinger```.
- Sometime you need to store your data in a persistent file system. When this need arises, use the ```VOLUME``` instruction as such ```VOLUME /path/to/directory```.<br>
  The /path/to/directory is a path to a directory used inside the image. When a container is created using the docker run command, the ```-v``` switch can be used to map this directory to an actual volume on the host system.
  This is only an indication. By default, if the user doesn’t map this volume to an external store for the container, the data will be stored inside the container.
- You can make this explicit using an EXPOSE instruction: ```EXPOSE 80```. <br>
  Using this instruction is purely for documentation purposes. It will NOT open a port to the outside world when a container is created from that image. 
  Anyone who creates a container will need to explicitly bind that port to an actual port of the host machine using the -p switch of the docker run command.

  

