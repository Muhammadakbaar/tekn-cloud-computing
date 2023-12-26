
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

![02](image/img2.png)

### Create a Deployment
1. Use the kubectl create command to create a Deployment that manages a Pod. The Pod runs a Container based on the provided Docker image. <br>
![03](image/img3.png)
2. View the Deployment: <br>
![04](image/img4.png)
3. View the Pod: <br>
![05](image/img5.png)
4. View cluster events:<br>
![06](image/img6.png)
5. View the kubectl configuration:<br>
![07](image/img7.png)

### Create a Service
1. Expose the Pod to the public internet using the kubectl expose command: <br>
![08](image/img8.png)
2. View the Service you created: <br>
![09](image/img9.png)
3. Run the following command: <br>
![10](image/img10.png)

### Enable addons
1. List the currently supported addons: <br>
![11](image/img11.png)
2. View the Pod and Service you created by installing that addon: <br>
![12](image/img12.png)

### Clean up
1. Now you can clean up the resources you created in your cluster: <br>
![13](image/img13.png)
2. Stop the Minikube cluster: <br>
![14](image/img14.png)
