# Docker: reference on how to use docker
[Tutorial](https://github.com/docker/labs/blob/master/beginner/chapters/alpine.md)

Most useful commands
- a container is a running image
- ```docker pull image```
- ```docker run command```
	- run command from image and stream output
	- ```-d```: detached mode
- ```docker run -it /bin/sh ```
	- run interactive shell from image
- ```docker ps```
	- see currently running containers
- ```docker stop id```: stop container
- ```docker rm id```: delete container
- ```docker image prune``` : remove all dangling [images](https://stackoverflow.com/questions/33913020/docker-remove-none-tag-images)
- before re-starting the image with the same name must ```rm``` container
- before re-building the image with the same name must ```rmi``` image, might need to ```-f``` it

Create your own image
- Write a Dockerfile
	```Docker
	# base image: can be anything https://hub.docker.com/
	FROM alpine:3.5

	# Install dependencies: python and pip
	RUN apk add --update py3-pip
	# python modules
	COPY requirements.txt /usr/src/app/
	RUN pip install --no-cache-dir -r /usr/src/app/requirements.txt

	# copy dependencies
	COPY app.py /usr/src/app/
	COPY templates/index.html /usr/src/app/templates/

	# tell the port number the container should expose
	EXPOSE 5000

	# run the application
	CMD ["python", "/usr/src/app/app.py"]
	```
- ```docker build -t kmjoshi/appname .``` : build app
- ```docker run -p 8888:5000 --name appname kmjoshi/appname``` : run app
- load app:
	- check ip: ```docker-machine ip default```
	- ip:8888
	- ip = 192.168.99.100

Loading a docker app on AWS
