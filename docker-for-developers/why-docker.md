# Why Docker?

- When a server application needs to handle a higher usage than what a single server can handle, the solution is well-known, place a reverse proxy in front of it, and duplicate the server as many times as needed.
- When using an orchestrator, you merely need to state how many containers you want and the image name and the orchestrator creates that many containers on all of your Docker servers. 
- By using containers, it’s a simple matter of telling the orchestrator that you want to run a new image version, and it gradually replaces every container with another one running the new version. Whatever technology
  stack is running inside the containers, telling the orchestrator that you want to run a new image version is a simple command (in fact, by changing just one line, as we’ll see).
