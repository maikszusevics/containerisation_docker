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




## Creating index.html for nginx 

- move file from localhost to container

- delete the existing file

- send file.html from localhhost to container

- docker cp command  source-address destination-address
- access denied - 
