# Learn DevOps: CI/CD with Jenkins using Pipelines and Docker

Docker should be installed

    $ cd ~
    $ git clone https://github.com/marley-nodejs/Learn-DevOps-CI-CD-with-Jenkins-using-Pipelines-and-Docker

    $ cd Learn-DevOps-CI-CD-with-Jenkins-using-Pipelines-and-Docker/

    $ docker build -t jenkins-docker -f jenkins-docker.dokerfile .

    $ sudo su -

    #  chmod -R 777 /var/jenkins_home/
    #  chmod 777 /var/run/docker.sock

    # docker run -p 8080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock --name jenkins -d jenkins-docker

<br/>

    http://<host>:8080

<br/>

Manage Plugins:

    - CloudBees Docker Build and Publish

Freestyle project

![Jenkins](/img/pic1.png "Jenkins")

<br/>

### 6. Jenkins Pipelines

**4. Demo Jenkins pipelines with NodeJS and Docker**

Manage Plugins:

    - NodeJS
    - Job DSL

<br/>

New Item --> name: "nodejs docker pipeline" --> PipeLine

![Jenkins](/img/pic2.png "Jenkins")

![Jenkins](/img/pic3.png "Jenkins")

![Jenkins](/img/pic4.png "Jenkins")

![Jenkins](/img/pic5.png "Jenkins")

Inside file misc/Jenkinsfile replace 'dockerhub' on 'credential_id'.

And marley/docker-nodejs-demo on your.

Commit and push code.

<br/>

```
   stage('docker build/push') {
     docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
       def app = docker.build("marley/docker-nodejs-demo:${commit_id}", '.').push()
     }
   }

```

![Jenkins](/img/pic6.png "Jenkins")

![Jenkins](/img/pic7.png "Jenkins")

![Jenkins](/img/pic8.png "Jenkins")

<br/>

**6. Demo Build, test, and run everything in Docker containers**

misc/Jenkinsfile.v2

![Jenkins](/img/pic9.png "Jenkins")

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

**12. Sonarqube integration (java)**

Plugins:

    - Sonarqube Scanner for Jenkins

Docker-compose file:

    $ mkdir ~/vagrant-jenkins-sonarqube && cd vagrant-jenkins-sonarqube
    $ wget https://raw.githubusercontent.com/wardviaene/jenkins-course/master/docker-compose/docker-compose.yml

    $ docker-compose up
    $ docker-compose log -f sonarqube

    http://<host>:9000
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

---

**Marley**

<a href="https://jsdev.org">jsdev.org</a>
