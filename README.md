# Containerisation with Docker

### What is containerisation?
A software container encapsulates an application, often a single executable service or microservice along with its libraries, frameworks and other components.

Containers are a standardized unit of software that allows developers to isolate their app from its environment, solving the “it works on my machine” headache. For millions of developers today, Docker is the standard to build and share containerized apps on desktops and cloud.

### What is the difference between containerisation and virtualisation?
Virtualization enables you to have multiple machines with different operating systems on the hardware, while containerization enables you to deploy multiple applications using the same operating system on a single virtual machine or server. 

![image](https://user-images.githubusercontent.com/110176257/189632002-0e3750f6-78ad-447f-ab5c-5f8b3b73ee71.png)


Virtualisation is great for deploying applications that require the full functionality of an operating system or when you want to use different operating systems for different tasks. Containers are a better choice when you priotritise minimizing the number of servers you’re using for multiple applications.

## What is Docker?

Docker is a platform as a service product which uses techniques like OS-level virtualisation to deliver software in packages called containers.

Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications. It has methodologies for building, testing, and shipping, designed to reduce the delay between writing code and running it in production.

![image](https://user-images.githubusercontent.com/110176257/189629451-f717068f-695e-4b59-8811-733819864fd3.png)

Docker provides the ability to package and run an application in an isolated environment called a container. Containers are lightweight and contain everything needed to run the application, so you do not need to rely on what is currently installed on the localhost machine.

#### What is an image?

An image is a read-only template with instructions for creating a Docker container. 

To build your own image, you create a Dockerfile with a simple syntax for defining the steps needed to create the image and run it. Each instruction in a Dockerfile creates a layer in the image. When you change the Dockerfile and rebuild the image, only those layers which have changed are rebuilt. This is part of what makes images so lightweight, small, and fast, when compared to other virtualization technologies.


#### What is a docker container?

A container is a runnable instance of an image. You can create, start, stop, move, or delete a container using the Docker API or CLI. You can connect a container to networks, attach storage, or create a new image based on its current state.

By default, a container is relatively well isolated from other containers and its host machine.


### Benefits of containerisation
- Efficiency

Containerization is more efficient than virtualization. Whereas virtualization is distributing several operating systems on a single server, containerization is more flexible and granular. Containers require minimal startup times, allowing developers to run more containers on the same compute capacity as one virtual machine.


- Portability

Containers create an executable software package abstracted away from the host OS. It is not dependent upon the host OS, making it portable and allowing it to run consistently and uniformly across any platform or cloud.

- Agility


- Faster app startup
- Easier management



## Whos is using docker?
Docker is used by over 50,000 companies worldwide:

![image](https://user-images.githubusercontent.com/110176257/189631180-078679b7-3ba2-4acf-9bc1-267e141a9488.png)

Some of the biggest companies using Docker include:

- Dailymotion
- Red Hat
- Business Insider 
- Spotify 
- Yelp 
- eBay 
- The New York Times 
- Oxford University Press
- PayPal 
- Sage
- Shopify
- The Washington Post 
- Uber


## Docker commands:

- `docker images` will list all images you have stored locally.
- `docker ps` lists current running containers. `-a` at the end will show stopped ones too.
- `docker run -d -p port:port imagename` will create a container and start the image. `-d` makes it detached, so you can still use the terminal after running the command.
- `docker stop ID_of_container` stops container.
- `docker start ID_of_container` starts stopped container.
- `docker rm ID_of_container -f` forcefully deletes container.
- `docker rmi Image_ID -f` forcefully deletes image.
- `docker exec -it ID_of_container bash` the `-it` stands for "interactive" and it will let you control and run commands in the container, kind of like SSHing into a VM.
- `docker build -t dockerhubname/imagename:versiontag` this builds an image.
- `docker push dockerhubname/imagename` this pushes an image to a dockerhub repo.
## Building an image 
To build an image from an edited nginx container, I used the steps in [this guide](https://www.dataset.com/blog/create-docker-image/) (starting from step 6)




## Creating index.html for nginx 

Editing the index.html file of the default nginx container will customize the webpage shown by the container.
The file is located at `/usr/share/nginx/html/`.

To edit this file, you may have to install updates as well as sudo and nano.

In order to automate this, you can create a index.html file locally and then move it to the container with a command.

move file from localhost to container using `docker cp index.html [imageID]:/usr/share/nginx/html`

This will replace the existing file with the one you've edited


## Automation with Dockerfile

Created a Dockerfile which will create a container and execute commands in order to provision app container.

```dockerfile
# select base image 
FROM nginx
# label it
LABEL MAINTAINER=maikszuse@gmail.com 
# copy data from localhost to container
COPY index.html /usr/share/nginx/html/
# allow required port
EXPOSE 80
# execute required command
CMD ["nginx", "-g", "daemon off;"]

```


### Building a Docker image for our Node app
- create a micro-service for node-app
- dockerfile inside app folder
- create a script to package our node app 
- create container of our image
- should load it on port 3000 or port 80
- push to docker hub

### Steps
- Copy app folder from a working nodeapp
- Create dockerfile in the same location as app folder
```dockerfile
# base image
FROM node
# label
LABEL MAINTAINER=MAIKS
# inside the container what would be the default working directory
# pwd 
# wrkdir /usr/src/app
WORKDIR /usr/src/app
# copy dependencies - app folder
COPY package*.json ./
# copy all files with .json to working directory
# run npm commands
RUN npm install  -g npm@7.20.6

# COPY EVERYTHING FROM CURRENT LOCATION & PASTE IN DEFAULT LOCATION
COPY . .
# expose the port
EXPOSE 3000

# cmd ["node","app.js"]
CMD ["node", "app.js"]
```
- Run docker commit and docker build to save it as image
- Run docker run command using port 3000 for nodeapp
- Use docker push command to upload image to dockerhub