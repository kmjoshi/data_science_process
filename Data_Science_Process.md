An effort to better define my Data Science process

# Outline
- ETL (Extract-Transform-Load)
	- [OpenRefine](https://github.com/OpenRefine/OpenRefine/wiki/Documentation-For-Users)
	- SQL/pandas helper functions
- EDA
	- Tableau
	- Grafana/Apache Superset 
- Stats
	- Viewing a distribution
	- Testing for effects (post-hoc)
- ML
	- Classification
		- [text-classification](https://github.com/kmjoshi/text_classification)
	- Clustering
	- Regression
	- Time-series forecasting (LSTM time-series forecasting)
- Deploying
	- [Docker](#Docker)
- Presenting results
	- How to decide what visualizations to use: [cheatsheet](./Franconeri_ExperCeptionDotNet_ChartChooser.pdf)
- [Pitch](#Pitch)

# Docker
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

<!-- # Pitch
Hi! I am Keshav Joshi, lover of all things, free-thinking, generally nice person, GaTech Alum, holder of two Masters Degrees (Physics/CS) and am looking for Data Science work of all kinds (full-time/part-time/contract).

This [link]() outlines my view of the Data Science process, with examples of work I have done with each.

Non-technical Data Science Process:
- Do you have data?
	- Yes!
		- Do you want a [post-hoc](https://stats.stackexchange.com/questions/129992/what-is-the-problem-with-post-hoc-testing) analysis of factors? Not advised! Design research questions first! (cite)
		- Do you want descriptive analysis of existing processes! Done let's hook it up to Tableau/any other dashboard tool!
	- No :/
		- Design research questions!
		- Design surveys/data input streams that would help answer those questions!
- Where's the ML/AI?
	- Do you need ML/AI?
		- Are the standard industry practices for answering those questions not sufficient?
		- Is this a repeated process with mostly objective answers?
			- Yes! Perfect for implementing AI
	- What can you do with ML?
		- Video: [Part 1](https://www.coursera.org/learn/ai-for-everyone/lecture/rv1fW/what-machine-learning-can-and-cannot-do), [Part 2](https://www.coursera.org/learn/ai-for-everyone/lecture/9n83j/more-examples-of-what-machine-learning-can-and-cannot-do). can audit this course to access
		- Segment data into clusters that might/might not be human-identifiable
		- Predict the ```FUTURE!```
	- Can I use classical AI techniques or control theory?
		- Is this a Constraint-satisfaction problem?
		- Is this an optimization problem?

Issues with the Data Science Process that I cannot handle but would like to learn!
- Putting a model into production and concurrently serving many customers
- Retraining a model with streaming/batch data. ```model drift```: when a model optimizes for new data and loses accuracy on original data set
	- Versioning?
- 

<!-- Oh you are still reading this! I appreciate this a lot, but you know what I would appreciate even more!? Some paisa $_$, please send some over if you felt this has helped you: [paytm]() [paypal](). -->

<!-- Thanks for reading! Suggestions welcome! 

Looking for roles! [Email me](mailto:kjoshfree@gmail.com) -->

# References
- [AI for Everyone by Andrew Ng](https://www.coursera.org/learn/ai-for-everyone)
- [Artificial Intelligence: A Modern Approach](http://aima.cs.berkeley.edu/)
