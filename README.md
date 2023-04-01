
# Jenkins Infrastructure

This repo used to build Jenkins using terraform in Ec2 instance in aws.



## 

The infra of jenkis is very simple, It consits of the following:
- VPC
- Public Subnet
- Internet gateway
- Route table
- EC2
I used in userdata of EC2 the following commands that I will use after that in jenkins:




install jenkins

```bash
sudo yum update
sudo wget -O /etc/yum.repos.d/jenkins.repo \
https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
sudo yum upgrade -y
sudo amazon-linux-extras install java-openjdk11 -y
sudo yum install jenkins -y
sudo systemctl enable jenkins
sudo systemctl start jenkins
```
install gettext
```bash
sudo yum install gettext -y
```
install docker
```bash
sudo yum search all docker
sudo yum info docker
sudo yum install docker
sudo usermod -a -G docker ec2-user
sudo systemctl enable docker.service
sudo systemctl start docker.service
```
install terraform
```bash
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
sudo yum -y install terraform
```
install kubectl
```bash
sudo curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.23.6/bin/linux/amd64/kubectl
sudo chmod +x ./kubectl
sudo mkdir -p $HOME/bin && sudo cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin
```
