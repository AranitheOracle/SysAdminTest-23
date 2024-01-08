# SAIC SysAdminTest'23

## Challenge 2 - Docker Monitoring & Scripting

Here we are tasked to monitor the docker containers and send an email to saic@students.iitmandi.ac.in when the container changes state from normal/running.

##### EmailAutomation

So for the email autoamtion script I took help from [GeekForGeeks](https://www.geeksforgeeks.org/how-to-send-automated-email-messages-in-python/). I used the services of [STMP2GO](https://www.smtp2go.com/).
The code for the email sender : [emailautomation.py]

#### MonitoringContainers

Now it was time for the monitoring part. Intitially I thought of shell scripting. Using docker commands of `(docker ps -a --format "{{.ID}}")` and `(docker ps -a --format "{{.Status}}")` to get the ID and Status so that when there is a Status change from UP to Exited it will run the [emailautomation.py] using `python3 emailautomation.py`. Things got a bit messy cause I guess my knowledge is too low (atleast they are not zero due to [**Network Chuck**](https://youtube.com/playlist?list=PLIhvC56v63IKioClkSNDjW7iz-6TFvLwS&si=TlVexjvb_uF1X9xB)).

Then I was googling stuff about dockers and came to knwo we can code about dockers in **Python**. Just need to run `pip install docker` to install the docker module. One more search led to me to: (https://github.com/docker/docker-py/tree/main
) which eventually led me to: (https://docker-py.readthedocs.io/en/stable/containers.html). Then little more surfing and scratching for details helped me gather all the information required to learn about the different fucntions of this module and similarity to the docker commands. 

