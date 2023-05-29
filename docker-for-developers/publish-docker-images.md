# Publish Docker Images

- The ```docker tag``` doesn’t duplicate the image contrary to running docker build again.
- The docker tag command accepts two arguments; first, the name of an existing image, and second, the name you want to add to that image. Example: ```docker tag webserver learnbook/webserver``` <br>
  I now have a single Docker image known by my machine under two names: webserver and short_name/webserver. When I run the docker image ls command, it will appear as two separate lines.
  The image ID is the same for both lines, which means there really is just one image on my machine, known under two different names.
- In order to reduce the size of an image, you need to understand that it is influenced by several factors:
    - The files included in your image
    - The base image size
    - Image layers
- You may want to exclude files from that copy. You can use a ```.dockerignore``` file for that purpose.
- Simply add a .dockerignore file at the root of your build context that lists files and folders that should be excluded from the build like a .gitignore file.
- Example ```.dockerignore``` file:
  ```
  # Ignore .git folder
  .git
  # Ignore Typescript files in any folder or subfolder
  **/*.ts
  ```
- When creating an image, Docker reads each instruction in order and the resulting partial image is kept separate; it is cached and labeled with a unique ID. 
  Such caching is very effective because it is used at different moments of an image life:
  - In a future build, Docker will use the cached part instead of recreating it as long as it is possible.
  - When pushing a new version of the image to a Registry, the common part is not pushed.
  - When pulling an image from a registry, the common part you already have is not pulled.
- Bad One:
  ```
  FROM debian:8

  COPY . .

  RUN apt-get update -y && apt-get upgrade -y && apt-get dist-upgrade -y
  RUN apt-get install -y php5
  ```
  Good One:
  ```
  FROM debian:8

  RUN apt-get update -y && apt-get upgrade -y && apt-get dist-upgrade -y
  RUN apt-get install -y php5

  COPY . .
  ```