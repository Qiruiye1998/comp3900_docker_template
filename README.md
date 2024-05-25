# COMP3900 Docker Installation Template

**Due in Week 3 Lab time.**

In this course, you must use Docker. To make sure you have everything set up and can run docker comfortably, you will need to complete this short exercise and show your tutor in Week 3 lab time.

**Successful completion of this task is required for your participation mark in Week 3**

# Step 1: Installing Docker

You can download docker at the following https://docs.docker.com/get-docker/
Once you download and install it, open it and ensure it is running whenever you are developing your code.

# Step 2: Clone this repo

Clone this repo (if you don't know how to do this, refer to the Git primer which you are also required to complete by Week 3 lab time)

# Step 3: Run the container

Run

```docker-compose up```

It might take a while for it to install everything required (2-5 mins is normal)

# Step 4: Testing that everything is working

Go to `localhost:3333` on a web browser and if everything is working it should display `Test: PASSED`


Please ensure you have completed this early so that if you have issues, we have time to help you on Ed forum or in your Week 2 lab.

## What is actually happening above?

Our goal with creating a Docker container is to bundle up all dependencies required to run an application along with the application itself. This means that you can specify all instructions needed to run your application, any depedencies it needs (e.g. Python3.11, Flask library etc) and run it on any device that has Docker installed regardless of the OS or the dependencies being present on that laptop.

To get our container, we need to create a Docker image which is a set of instructions to run our container. This first involves creating a Dockerfile which defines the instructions for setting up the application environment. Then you can turn this into an image and run the container using `docker run`. Detailed instructions for how to structure your Dockerfile can be found in each of the Dockerfiles in this repo.

## What about docker-compose?

The application we made in this repo is much more complicated - it contains a frontend and a backend which are each their own containers. We can use `docker-compose.yml` to specify exactly what services we want to run to make this application function. Each of these services must either have a pre-built image or you must have a Dockerfile for it. In the case of this repo, you can see that the frontend and backend each have their own Dockerfile that specifies exactly what is needed for each container. Then, if you look back to `docker-compose.yml` you can see that we define the services we want, any environment variables, whether we want to map any internal ports to external ports etc. You can find a full list of things you can specify online.

After we create this file, we can use `docker-compose up` which will install any new dependencies (it may take a while the first time you run it) and then run the application.
