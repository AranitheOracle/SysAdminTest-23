# SAIC SysAdminTest'24

## Challenge 4 - Docker & Networking

Here we are tasked to pull an image from [**Docker Hub**](https://hub.docker.com/search?q=). Then we need to balance the load between multiple instances of the same image.

For the first part code is very basic. Just some known Docker commands like `pull` and `run` are used as you can see below.
For this I used [this image (lightweight)](https://hub.docker.com/r/metavinayak/matrix) .
~~~
#!/bin/bash
img_id="d8e1f39c17d0"
echo "Let's pull the image first"
sleep 1
docker pull metavinayak/matrix
sleep 3
echo "Enter the number of instances of the image you want to create : "
read num
for ((i=1; i<=$num; i++)); do
    docker run -d --name instance${i} --network my_network -p 808$i:3000 $img_id
done
~~~
The [demonstration](Screenshots/part1demonstration.png) and the [script](part1initial.sh) are attached.
