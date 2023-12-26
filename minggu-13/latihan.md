
# **Hello Minikube**
This tutorial shows you how to run a sample app on Kubernetes using minikube. The tutorial provides a container image that uses NGINX to echo back all the requests.

# Objectives 
* Deploy a sample application to minikube.
* Run the app.
* View application logs.

# Before you begin 
This tutorial assumes that you have already set up minikube. See minikube [start for]([url](https://minikube.sigs.k8s.io/docs/start/)) installation instructions.
You also need to install kubectl. See [Install tools]([url](https://kubernetes.io/docs/tasks/tools/#kubectl)) for installation instructions.


## Create a minikube cluster
1. Run this command ``` minikube start ``` <br>
![01](gambar-01.jpg)

## Open the Dashboard
1. Open new terminal and run <br>
![02](gambar-02.jpg)

## Create a Deployment
1. Use the kubectl create command to create a Deployment that manages a Pod. The Pod runs a Container based on the provided Docker image <br>
![03](gambar-03.jpg)

2. View the Deployment <br>
![04](gambar-04.jpg)

3. View the Pod <br>
![05](gambar-05.jpg)

4. View cluster events <br>
![06](gambar-06.jpg)

5. View the kubectl configuration <br>
![07](gambar-07.jpg)

6. View application logs for a container in a pod <br>
![07](gambar-08.jpg)

## Create a Service

1. Expose the Pod to the public internet using the kubectl expose command <br>
![08](gambar-09.jpg)

2. View the Service you created <br>
![09](gambar-10.jpg)

3. Run the following command <br>
![10](gambar-11.jpg)

4. This opens up a browser window that serves your app and shows the app's response <br>
![11](gambar-12.jpg)

## Enable addons
1. List the currently supported addons <br>
![11](gambar-13.jpg)

2. Enable an addon, for example, ``` metrics-server ``` <br>
![11](gambar-14.jpg)

3. View the Pod and Service you created by installing that addon <br>
![12](gambar-15.jpg)

4. Check the output from ``` metrics-server ``` <br>
![12](gambar-16.jpg)

5. Disable ``` metrics-server ``` <br>
![12](gambar-17.jpg)

## Clean up

1. Now you can clean up the resources you created in your cluster <br>
![12](gambar-18.jpg)
