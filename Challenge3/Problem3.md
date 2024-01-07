# SAIC SysAdminTest'24 

## Challenge 3 - Docker Deployments
Here we are given two websites and we need to deploy them using docker containers.
We also need to Backup a volume mapped data as a zip file everyday at 11:55 pm.
At first let's go through the each website on by one.

### [SAIC-website](https://github.com/KamandPrompt/SAIC-Website)

After opening the github page , we can see that it is a basic html-css-js based website which was also mentioned in the task.
I took some help from this video from **freecodecamp** (https://youtu.be/Wf2eSG3owoA?si=HStbjamGQYug83Fi).
For hosting this I used the `nginx:latest` as base image to build.   
Then I created a *Dockerfile* with the following contents :---[DockerFile1](Dockerfile1)
~~~
FROM nginx:latest
ADD . /usr/share/nginx/html
~~~
I built an image named website using `docker build --tag website:latest` . 
Finally I ran the image to host the website using `docker run --name SAIC -d -p 9000:80 website:latest .`

### [Github Languages](https://github.com/alex-benoit/github-languages.git)

This website is based on Ruby-on-Rails.
So I need to built a image using `ruby` as the base image. I google how to do it and went through a lot of articles and websites.
Then taking information from this: (https://earthly.dev/blog/rails-with-docker/) I tried to built an image based on  `ruby:alpine`.

I used the below as the initial Dockerfile:
~~~
FROM ruby:alpine3.19
  RUN apk add \
    build-base \
    postgresql-dev \
    tzdata \
    nodejs
  
  WORKDIR /app
  COPY Gemfile* .
  RUN bundle install
  COPY . .
  EXPOSE 3000
  CMD ["rails", "server", "-b", "0.0.0.0"]
~~~
After running `docker build --tag webs:latest` it threw errors. Basically because of the version dependencies. I made some changes to make the above code run. All efforts were in vain[Error](Screenshots/error.png)