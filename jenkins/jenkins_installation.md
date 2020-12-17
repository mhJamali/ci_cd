**Install Jenkins on AWS EC2**

Jenkins is a self-contained Java-based program, ready to run out-of-the-box, with packages for Windows, Mac OS X and other Unix-like operating systems. As an extensible automation server, Jenkins can be used as a simple CI server or turned into the continuous delivery hub for any project.

**Prerequisites**

EC2 Instance With Internet Access & Security Group with Port 8080 open for internet

Java v1.8.x

**Install Java**

1. yum install java-1.8*

2. Confirm Java Version and set the java home

java -version

find /usr/lib/jvm/java-1.8* | head -n 3

JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-<Java version which seen in the above output>

export JAVA_HOME

PATH=$PATH:$JAVA_HOME
 To set it permanently update your .bash_profile

vi ~/.bash_profile

**Install Jenkins**

Get the latest version of jenkins from https://pkg.jenkins.io/redhat-stable/ and install

yum -y install wget

sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo

sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key

yum -y install jenkins


Start Jenkins

service jenkins start

**Accessing Jenkins**

By default jenkins runs at port 8080, You can access jenkins at
http://YOUR-SERVER-PUBLIC-IP:8080

**Configure Jenkins**

The default Username is admin

Grab the default password

Password Location:/var/lib/jenkins/secrets/initialAdminPassword

Skip Plugin Installation; We can do it later

Change admin password

    Admin > Configure > Password
    
Configure java path

    Manage Jenkins > Global Tool Configuration > JDK

Create another admin user id

**Test Jenkins Jobs**

Create “new item”

Enter an item name – My-First-Project

Chose Freestyle project

Under the Build section Execute shell: echo "Welcome to Jenkins Demo"

Save your job

Build job

Check "console output"
