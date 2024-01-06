# SAIC SysAdminTest'24 

## Challenge 3 - Docker Deployments
Here we are given two websites and we need to deploy them using docker containers.
We also need to Backup a volume mapped data as a zip file everyday at 11:55 pm.
At first let's go through the each website on by one.

### [SAIC-website](https://github.com/KamandPrompt/SAIC-Website)

After opening the github page , we can see that it is a basic html-css-js based website which was also mentioned in the task.
I took some help from this video from **freecodecamp** (https://youtu.be/Wf2eSG3owoA?si=HStbjamGQYug83Fi).
For hosting this I used the `nginx:latest` as base image to build.   
Then I created a *Dockerfile* with the following contents :--- ][Dockerfile](Challenge3/Screenshots/dockerfile1.png)
~~~
FROM nginx:latest
ADD . /usr/share/nginx/html
~~~
I built an image named website using `docker build --tag website:latest` . 
Finally I ran the image to host the website using `docker run --name SAIC -d -p 9000:80 website:latest .`
