## Docker EC2 Deploy Sample

### 1. yum update to update rpm package in EC2
```
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
sudo amazon-linux-extras install docker
```

### 3. Start Docker
```
sudo service docker start
```

### 4. Push local docker image to Docker Hub
```
docker build -t <image-name> .

docker tag <image-name> <docker-hub-username>/<dockerhub-repository-name>

docker login

docker push <docker-hub-username>/<dockerhub-repository-name>
```