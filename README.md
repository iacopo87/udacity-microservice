# Udagram Image Filtering Microservice

Udagram is a simple cloud application developed alongside the Udacity Cloud Engineering Nanodegree. It allows users to register and log into a web client, post photos to the feed, and process photos using an image filtering microservice.

The project is split into three parts:

1. [The Simple Frontend](/udacity-c3-frontend)
   A basic Ionic client web application which consumes the RestAPI Backend.
2. [The RestAPI Feed Backend](/udacity-c3-restapi-feed), a Node-Express feed microservice.
3. [The RestAPI User Backend](/udacity-c3-restapi-user), a Node-Express user microservice.

### Setup Docker Environment

Once you have installed Docker on your local machine, open a new terminal and:

1. Move to docker folder: `cd udacity-c3-deployment/docker`
2. Build the images: `docker-compose -f docker-compose-build.yaml build --parallel`
3. Push the images: `docker-compose -f docker-compose-build.yaml push`
4. Run the container: `docker-compose up`

### Setup k8s Environment

I used MiniKube to run the cluster locally. After Minikube is installed end configured:

1. Move to k8s folder: `cd udacity-c3-deployment/k8s`
2. Start minikube: `minikube start`
3. Set environment variable for terminal: `eval $(minikube docker-env)`
4. Apply each file in the directory with kubectl: `kubectl apply -f <file-name>.yaml`
5. Port forward for reverse proxy: `kubectl port-forward service/reverseproxy 8080:8080`
6. Port forward for frontend: `kubectl port-forward service/frontend 8100:8100`
7. Enjoy your app locally: `http://localhost:8100/`

p.s In the repo I didn't commit the real value for the secrets
