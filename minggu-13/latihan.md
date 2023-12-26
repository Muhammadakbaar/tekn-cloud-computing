
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
1. Run this command ``` minikube start ```

![01](gambar-01.jpg)

## Open the Dashboard
1. Open new terminal and run

![02](gambar-02.jpg)

## Create a Deployment
1. Use the kubectl create command to create a Deployment that manages a Pod. The Pod runs a Container based on the provided Docker image
   
![03](gambar-03.jpg)

2. View the Deployment
   
![04](gambar-04.jpg)

3. View the Pod
   
![05](gambar-05.jpg)

4. View cluster events
   
![06](gambar-06.jpg)

5. View the kubectl configuration
    
![07](gambar-07.jpg)

6. View application logs for a container in a pod
   
![07](gambar-08.jpg)

## Create a Service

1. Expose the Pod to the public internet using the kubectl expose command
   
![08](gambar-09.jpg)

3. View the Service you created
   
![09](gambar-10.jpg)

4. Run the following command
   
![10](gambar-11.jpg)

5. This opens up a browser window that serves your app and shows the app's response
![11](gambar-12.jpg)

## Enable addons
1. List the currently supported addons
   
![11](gambar-13.jpg)

2. Enable an addon, for example, ``` metrics-server ```

![11](gambar-14.jpg)

3. View the Pod and Service you created by installing that addon
   
![12](gambar-15.jpg)

4. Check the output from ``` metrics-server ```

![12](gambar-16.jpg)

5. Disable ``` metrics-server ```

![12](gambar-17.jpg)

## Clean up

1. Now you can clean up the resources you created in your cluster

![12](gambar-18.jpg)
