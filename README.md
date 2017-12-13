# Docker-Tutorial

This is a tutorial to learn how to deploy a very simple static website using Docker. 

Lets begin.

## Step 1:
Create a directory **"Docker Tutorial"** which will contain your docker image resources.

## Step 2:
Go inside the directory and create **Dockerfile**. It is the base file for building your docker image. Paste the following content in it.

```FROM nginx:alpine
COPY . /usr/share/nginx/html
```

In this example, our base image is the Alpine version of Nginx. This provides the configured web server on the Linux Alpine distribution.

The first line defines our base image. The second line copies the content of the current directory into a particular location inside the container.

## Step 3:
Now create index.html file with the following content.

```<!DOCTYPE html>
<html lang="en">
<head>
  <title>Docker Tutorial </title>
</head>
<body>
  <h4>Welcome to Docker Tutorial</h4>
  <p>This is a docker container running Alpine version of Nginx.</p>

</body>
</html>
```

## Step 4:
Now it is time to build our static HTML image using the build command below.

```docker build -t <repository_name>:<tag> .```

Example: ```docker build -t docker_website:v1 .```

You can also view all the docker images (including theone you just created) with the below command.

```docker images```

## Step 5:
Lets launch our newly built image. In this case, I am binding port 80 to our host using the -p parameter.

```docker run -d -p 8080:80 docker_website:v1```

Now open http://localhost:8080 in your browser.

To stop a detached container, run `docker stop` by giving the container ID.


You can skip all the above steps and straight away deploy a static site on Docker as I've already created the image that we are using here and hosted on the registry - pramaniksuvam/docker-tutorial. You can download and run the image directly in one go using docker run.

```docker run -d -p 5050:80 pramaniksuvam/docker-tutorial```


