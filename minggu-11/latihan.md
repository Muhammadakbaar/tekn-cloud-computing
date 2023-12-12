### Stage Setup
1. Let’s get started by first cloning the demo code repository, changing the working directory, and checking the demo branch out.
![01](gambar-01.png)

### Step 0: Basic Link Extractor Script
1. Checkout the step0 branch and list files in it.
![02](gambar-02.png)
2. The linkextractor.py file is the interesting one here, so let’s look at its contents:
![03](gambar-03.png)
3. However, this seemingly simple script might not be the easiest one to run on a machine that does not meet its requirements. The README.md file suggests how to run it, so let’s give it a try:
![04](gambar-04.png)
4. When we tried to execute it as a script, we got the Permission denied error. Let’s check the current permissions on this file:
![05](gambar-05.png)
5. We can either change it by running chmod a+x linkextractor.py or run it as a Python program instead of a self-executing script as illustrated below:
![06](gambar-06.png)

### Step 1: Containerized Link Extractor Script
1. Checkout the step1 branch and list files in it.
![07](gambar-07.png)
2. We have added one new file (i.e., Dockerfile) in this step. Let’s look into its contents:
![08](gambar-08.png)
3. So far, we have just described how we want our Docker image to be like, but didn’t really build one. So let’s do just that:
![09](gambar-09.png)
4. We have created a Docker image named linkextractor:step1 based on the Dockerfile illustrated above. If the build was successful, we should be able to see it in the list of image:
![10](gambar-10.png)
5. Now, let’s run a one-off container with this image and extract links from some live web pages:
![11](gambar-11.png)
6. Let’s try it on a web page with more links in it:
![12](gambar-12.png)

### Step 2: Link Extractor Module with Full URI and Anchor Text
1. Checkout the step2 branch and list files in it.
![13](gambar-13.png)
2. Let’s have a look at the updated script:
![14](gambar-14.png)
3. Now, let’s build a new image and see these changes in effect:
![15](gambar-15.png)
4. We have used a new tag linkextractor:step2 for this image so that we don’t overwrite the image from the step1 to illustrate that they can co-exist and containers can be run using either of these images.
![16](gambar-16.png)
5. Running a one-off container using the linkextractor:step2 image should now yield an improved output:
![17](gambar-17.png)
6. Running a container using the previous image linkextractor:step1 should still result in the old output:
![18](gambar-18.png)

### Step 3: Link Extractor API Service
1. Checkout the step3 branch and list files in it.
![19](gambar-19.png)
2. Let’s first look at the Dockerfile for changes:
![20](gambar-20.png)
3. The linkextractor.py module remains unchanged in this step, so let’s look into the newly added main.py file:
![21](gambar-21.png)
4. It’s time to build a new image with these changes in place:
![22](gambar-22.png)
5. We are also assigning a name (--name=linkextractor) to the container to make it easier to see logs and kill or remove the container.
![23](gambar-23.png)
6. If things go well, we should be able to see the container being listed in Up condition:
![24](gambar-24.png)
7. We can now make an HTTP request in the form /api/<url> to talk to this server and fetch the response containing extracted links:
![25](gambar-25.png)
8. Since the container is running in detached mode, so we can’t see what’s happening inside, but we can see logs using the name linkextractor we assigned to our container:
![26](gambar-26.png)
9. We can see the messages logged when the server came up, and an entry of the request log when we ran the curl command. Now we can kill and remove this container:
![27](gambar-27.png)

### Step 4: Link Extractor API and Web Front End Services
1. Checkout the step4 branch and list files in it. <br>
![28](gambar-28.png)
2. So let’s look at the docker-compose.yml file we have: <br>
![29](gambar-29.png)
3. Now, let’s have a look at the user-facing www/index.php file:
![30](gambar-30.png)
4. Let’s bring these services up in detached mode using docker-compose utility:
![31](gambar-31.png)
5. We should now be able to talk to the API service as before:
![32](gambar-32.png)
6. Before we move on to the next step we need to shut these services down, but Docker Compose can help us take care of it very easily:
![33](gambar-33.png)

### Step 5: Redis Service for Caching
1. Checkout the step5 branch and list files in it. <br>
![34](gambar-34.png)
2. Let’s first inspect the newly added Dockerfile under the ./www folder: <br>
![35](gambar-35.png)
3. Next, we will look at the API server’s api/main.py file where we are utilizing the Redis cache:
![36](gambar-36.png)
4. Now, let’s look into the updated docker-compose.yml file: <br>
![37](gambar-37.png)
5. Let’s boot these services up: <br>
![38](gambar-38.png)
6. we can use docker-compose exec followed by the redis service name and the Redis CLI’s monitor command:
![39](gambar-39.png)
7. Now, shut these services down and get ready for the next step:
![40](gambar-40.png)

### Step 6: Swap Python API Service with Ruby
1. Checkout the step6 branch and list files in it. <br>
![41](gambar-41.png)
2. With these in place, let’s boot our service stack: <br>
![42](gambar-42.png)
3. We should now be able to access the API (using the updated port number):
![43](gambar-43.png)
4. We can use the tail command with the -f or --follow option to follow the log output live.
![44](gambar-44.png)
5. Since we have persisted logs, they should still be available after the services are gone:
![45](gambar-45.png)
