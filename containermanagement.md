# Container management

Pull an image from a registry:
```
sudo docker pull <repository:tag>
```
List installed images:
```
sudo docker image list
```
Run image as container:
```
sudo docker run <options> <image>
```
List running containers:
```
sudo docker ps
```
List all containers:
```
sudo docker ps -a
```
Stop container:
```
sudo docker stop <container>
```
Start container:
```
sudo docker start <container>
```
Save container as image:
```
sudo docker commit <options> <container> <image name>
```
Push image to registry:
```
sudo docker push <image>
```
Copy file into running container:
```
sudo docker cp <source path> <container:destination path>
```
Copy file from running container to host:
```
sudo docker cp <container:source path> <destination path>
```
Remove container:
```
sudo docker rm <container>
```
Remove image:
```
sudo docker rmi <image>
```
Remove unused containers, images, and networks:
```
sudo docker system prune
```
Remove all containers, images, networks:
```
sudo docker system prune -a
```


For more information, refer to the official Docker documentation: https://docs.docker.com/engine/reference/commandline/cli/