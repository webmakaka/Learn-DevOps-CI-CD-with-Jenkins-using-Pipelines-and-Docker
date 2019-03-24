# Learn DevOps: CI/CD with Jenkins using Pipelines and Docker

Docker should be installed

    # cd ~
    # git clone https://github.com/wardviaene/jenkins-docker
    # cd jenkins-docker
    # docker build -t jenkins-docker .

    #  chmod -R 777 /var/jenkins_home/
    #  chmod 777 /var/run/docker.sock

    # docker run -p 8080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock --name jenkins -d jenkins-docker


    http://<host>:8080

    # cat /var/jenkins_home/secrets/initialAdminPassword

Manage Plugins:

    - CloudBees Docker Build and Publish

Freestyle project

![Jenkins](/img/pic1.png "Jenkins")

<br/>

### 6. Jenkins Pipelines

misc/Jenkinsfile.v2

![Jenkins](/img/pic2.png "Jenkins")

<br/>

### 7. Jenkins Integrations

<br/>

**1. Email integration**

Plugins:

    - Email Extension Plugin

https://mailtrap.io/

Jenkins --> Configure --> Extended E-mail Notification

SMTP server: smpt.mailtrap.io

Use SMTP Authentication

Pipeline:

https://github.com/wardviaene/jenkins-course/blob/master/email-notifications/Jenkinsfile

<br/>

**12. Sonarqube integration**

Plugins:

    - Sonarqube Scanner for Jenkins

Docker-compose file:

    $ cd ~
    $ mkdir jenkins-sonarqube && cd jenkins-sonarqube
    $ wget https://github.com/wardviaene/jenkins-course/blob/master/docker-compose/docker-compose.yml

    $ docker-compose up
    $ docker-compose log -f sonarqube

    http://<host>:8000
    admin/admin

<br/>

    Sonarqube --> Admin --> Security

    Generate Tokens

    jenkins --> generate

<br/>

    Jenkins --> Global Tool Configuration

    Sonarqube Scanner: --> Name --> sonar
    Install automaticaly

    Credential --> Secret text

    Scope: global
    Secret: sonarqube token
    ID: sonar
    Description: sonar

<br/>

    New Pipeline Project

    Pipeline:

    https://github.com/wardviaene/jenkins-course/blob/master/sonarqube/Jenkinsfile

<br/>

### Other plugins

    - NodeJS
    - Job DSL

---

**Marley**

<a href="https://jsdev.org">jsdev.org</a>

email:  
![Marley](http://img.fotografii.org/a3333333mail.gif "Marley")
