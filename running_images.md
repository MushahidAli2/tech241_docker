# Running the image
To run a Docker image, use the command:
```bash
docker run hello-world
```

After running the image, Docker will check if we have this image on our local machine. If not, it will download the image from the online registry.
The output confirms that our Docker installation is working correctly.

Docker takes the following steps to generate the message:
1. The Docker client contacts the Docker daemon.
2. The Docker daemon pulls the "hello-world" image from the Docker Hub.
(amd64)
3. The Docker daemon creates a new container from that image, which runs the executable producing the output we see.
4. The Docker daemon streams that output to the Docker client, which sends it to our terminal.
   
## Running Nginx Image

To run an Nginx image, use the following command:
`docker run -d -p 80:80 nginx`
The `-p 80:80` option maps port 80 of the local host to port 80 of the Nginx container.

## Stopping and Starting Containers
```bash
docker stop <docker_id>
docker start <docker_id>
```
## Interacting with Containers
`docker exec -it <container_id> sh`
This opens an interactive shell within the container.

## Saving Changes to Docker Image and Pushing to Docker Hub:
To save the changes made to a Docker image and push the updated image to a Docker repository, you can follow these steps:

1. Make Changes to the Container: First, make the desired changes to the running Docker container. This could include modifying files, installing software, or making any other necessary changes for your application.

2. Commit Changes to a New Image: After making the changes to the container, create a new image from it using the docker commit command. This will incorporate the changes into the new image.
`docker commit <container_id> <new_image_name>:<tag>`

3. Tag the Image for the Repository: Next, tag the new image with the appropriate name and tag that matches your Docker repository using the docker tag command.
`docker tag <new_image_name>:<tag> username/repository:tag`

4. Push the Image to Docker Hub: Finally, push the updated image to Docker Hub using the docker push command:
`docker push username/repository:tag`

## Nginx Container using Dockerfile

To create an Nginx container using a Dockerfile, you can use the following Dockerfile:
```Dockerfile
# Select the base image of nginx
FROM nginx

# Label it
LABEL MAINTAINER=mushahid@sparta

# Copy index.html from localhost to the default nginx index.html location
COPY index.html /usr/share/nginx/html/

# Port mapping or exposing the required port
EXPOSE 80

# Command to launch the web server
CMD ["nginx", "-g", "daemon off;"]

```
## Node App Container using Dockerfile

For creating a Node.js application container using a Dockerfile, you can follow these steps:
```Dockerfile
# Step 1: Choose the base image with Node.js version 12
FROM node:12

# Step 2: Set the working directory inside the container
WORKDIR /app

# Step 3: Copy the application source code from localhost to the container
COPY app /app

# Step 4: Install dependencies
RUN npm install

# Step 5: Expose the port your Node.js app is listening on
EXPOSE 3000

# Step 6: Define the startup command for your app
CMD ["npm", "start"]

```
After that, you can build and run the Node.js application container as follows:

Build the Docker image:
`docker build -t mushahid12/tech241-sparta-app`

Run the container on port 3000:
`docker run -d -p 3000:3000 mushahid12/tech241-sparta-app`

