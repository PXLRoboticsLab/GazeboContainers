# GazeboContainers
# Install docker
```
$ sudo apt-get update
```
```
$ sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
```
```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
```
$ sudo apt-key fingerprint 0EBFCD88
```
```
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
 ``` 
 ```
$ sudo apt-get update
```
```
$ sudo apt-get install docker-ce
```


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

```
$ sudo docker pull prlcontainers.pxl.be/prl/<repository:tag>
```
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
