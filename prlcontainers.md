# Install docker

Update the package index:
```
$ sudo apt-get update
```

Install packages to allow to use a repository over HTTps:
```
$ sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
```

Add Docker's GPG key:
```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Set up the stable repository:
```
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
 ``` 
 
 Update the package index:
 ```
$ sudo apt-get update
```

Install Docker
```
$ sudo apt-get install docker-ce
```

Source: https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-docker-ce-1


# For CUDA/cuDNN images, install nvidia docker

Follow the instructions at https://github.com/NVIDIA/nvidia-docker



# Install the prlcontainers certificate
Go to prlcontainers.pxl.be and click on the small green lock next to the url.

![](https://i.imgur.com/CxgmJCa.png)

Go to More information > View Certificate > Details > Export

![](https://i.imgur.com/sWf0BfI.png)

Export the certificate to your home folder and run the following commands:
```
$ sudo mv prlcontainerspxlbe.crt /usr/local/share/ca-certificates/
```
```
$ sudo update-ca-certificates
```

# Make container

Pull the container image:
```
$ sudo docker pull <repository:tag>
```
Example: sudo docker pull prlcontainers.pxl.be/prl:eborghi10-ar.drone-ros


Enable showing GUI applications (__has to be executed after each restart__):
```
$ xhost +local:root
```

### For CUDA/cuDNN containers:
```
$ sudo docker run --runtime=nvidia -t -d --env="DISPLAY" --env="QT_X11_NO_MITSHM=1" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" <image>
```
### For regular containers:
```
$ sudo docker run -t -d --env="DISPLAY" --env="QT_X11_NO_MITSHM=1" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" <image>
```

#### To share a folder between host and container, add the following to the docker run command
```
 -v /path/on/host:/path/in/container
```
### Get the container id:
```
$ sudo docker ps -a
```
### Enter the container:
```
$ sudo docker exec -it <id> /bin/bash
```
