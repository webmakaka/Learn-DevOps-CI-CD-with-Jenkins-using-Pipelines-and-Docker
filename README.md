# Learn DevOps: CI/CD with Jenkins using Pipelines and Docker

Docker should be installed

    $ cd ~
    $ git clone https://github.com/wardviaene/jenkins-docker
    $ cd jenkins-docker
    $ docker build -t jenkins-docker .

    $ docker run -p 8080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/nun/docker.sock --name jenkins -d jenkins-docker

___

**Marley**

<a href="https://jsdev.org">jsdev.org</a>

email:  
![Marley](http://img.fotografii.org/a3333333mail.gif "Marley")
