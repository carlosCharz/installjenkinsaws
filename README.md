# Install Jenkins 2.x in AWS EC2 Instance (Amazon Linux AMI)

## Software to install
* Java 8
* Jenkins 2.x

## Check YUM Updates
```
sudo su
yum list installed
yum update
```

## Install Java 8
```
yum install java-1.8.0
yum remove java-1.7.0-openjdk
```

## Install Jenkins 2.x
1 Download Jenkins from the Red Hat Repository
```
wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo
```
2 Import the verification key using the package manager RPM
```
rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
```
3 Install Jenkins with yum command
```
yum install jenkins
```

## Start Jenkins Service
```
service jenkins start
```

## Jenkins Paths
1 To change the default port of Jenkins you need to edit the jenkins config file
```
vim  /etc/sysconfig/jenkins
```
2 Change the port according your desired configuration (vi commands: "i" for insert mode, "ESC" key to escape the inserting mode, ":wq" for write an quit) 
```
JENKINS_PORT=”8081″
```

## Check Jenkins Installation
* fuser: to display the process id(PID) of every process using the specified files
```
fuser -v -n tcp 8080
```
* netstat: to list out all the network (socket) connections on a system
```
netstat -na | grep 8080
```

## Set Auto Start for Jenkins Service
```
sudo chkconfig --list jenkins
sudo chkconfig jenkins on
```
