Reverse proxy is a server that sits between applications and clients. It is responsible for forwarding client requests to the appropriate server.

In this project, I set up a reverse proxy server using an nginx container image and created two simple WWW servers (one using nginx and the other using Apache). 
I used docker-compose to launch the containers, which simplified the setup and created a separate network for all the containers.

Dockerfile creates our own reverse proxy image based on the nginx:alpine container image. 
The custom nginx.conf file, configured manually, was copied into the container.

The upstream directive defines a group of servers that listen on different ports. 
When trying to access the host machine through port 8080, nginx acts as a reverse proxy and handles what is defined in the proxy_pass. 
In this case, it's docker-nginx. Similarly, when accessing through port 8081, the Apache service will be handled.

Using docker-compose allows us to run all the required containers simultaneously and keeps their configuration and dependencies in one place.

To start the system, use the command docker-compose up -d (-d runs the containers in the background).
The docker ps command will show us the running containers. Two of them are not directly accessible.
