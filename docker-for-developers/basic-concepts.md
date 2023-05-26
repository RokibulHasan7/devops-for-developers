# Basic Concepts

- There are three concepts: containers, images and registries.
- A ```container``` is what we eventually want to run and host in Docker. You can think of it as an isolated machine, or a virtual machine if you prefer. It contains everything it needs to run: OS, packages, 
  runtimes, files, environment variables, standard input, and output.
- Any container that runs is created from an image. An image describes everything that is needed to create a container; it is a template for containers. You may create as many containers as needed from a single image.
- Images are stored in a registry. In the example above, the app2 image is used to create two containers. Each container lives its own life, and they both share a common root: their image from the registry.
