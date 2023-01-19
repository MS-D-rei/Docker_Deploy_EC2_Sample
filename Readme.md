## Docker EC2 Deploy Sample

### 1. yum update to update rpm package in EC2
```
// EC2 login console
sudo yum update
```

#### what is yum?
yum stands for Yellowdog Updater Modified
http://yum.baseurl.org/

"Yum is an automatic updater and package installer/remover for rpm systems.
It automatically computes dependencies and figures out what things should occur to install packages.
It makes it easier to maintain groups of machines without having to manually update each one using rpm."

#### what is rpm?
RPM stands for Red Hat Package Manager.

Ref URL https://blog.packagecloud.io/what-is-rpm-and-how-do-i-use-it/

"The manager was designed to be used for Linux distributions.
Initially, it was made to be used in Red Hat Linux.
Now, it’s widely used in other Linux distributions including Fedora, CentOS, OpenSUSE, OpenMandriva, and Oracle Linux.
Most RPM files are binary with the compiled version of the software."

### 2. Install Docker in EC2 instance
```
// EC2 login console
sudo amazon-linux-extras install docker
```

### 3. Start Docker
```
// EC2 login console
sudo service docker start
```

### 4. Push local docker image to Docker Hub
```
// local
docker build -t <image-name> .

docker tag <image-name> <docker-hub-username>/<dockerhub-repository-name>

docker login

docker push <docker-hub-username>/<dockerhub-repository-name>
```

### 5. Run docker image pulling from public repository in Docker Hub
```
sudo docker run -dp 80:80 --rm <docker-hub-username>/<dockerhub-repository-name>
```
If EC2 instance doesn't have the docker image,
EC2 instance automatically tries to pull the image from Docker Hub.
If EC2 instance has the docker image,
EC2 instance use it when run docker run command.

confirm docker container is running or not.
```
// EC2 login console
sudo docker ps
```

### 6. EC2 security inbound setting
EC2 security has inbound and outbound setting.
inbound means access permission from somewhere to EC2 instance.
outbound means access permission from EC2 instance to somewhere.

For trial purpose, add HTTP IPv4 and IPv6 anywhere to the security policy in this time.

### 7. How to rebuild docker image
1. build local docker image
2. push it to Docker Hub
3. pull the image in EC2 instance console
```
// EC2 login console
sudo docker pull <docker-hub-username>/<dockerhub-repository-name>
```
4. run the image again