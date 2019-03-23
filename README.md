# Learn DevOps: CI/CD with Jenkins using Pipelines and Docker

Docker should be installed

    # cd ~
    # git clone https://github.com/wardviaene/jenkins-docker
    # cd jenkins-docker
    # docker build -t jenkins-docker .

    #  chmod 777 /var/jenkins_home/

    # docker run -p 8080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock --name jenkins -d jenkins-docker


http://<host>:8080
    
    # cat /var/jenkins_home/secrets/initialAdminPassword


Manage Plugins:

    - NodeJS
    - CloudBees Docker Build and Publish



Freestyle project



___

**Marley**

<a href="https://jsdev.org">jsdev.org</a>

email:  
![Marley](http://img.fotografii.org/a3333333mail.gif "Marley")
