# **Udemy Tutorial - Docker容器技术从入门到精通 Peng Xiao** 

**Author [Docker Tips](https://dockertips.readthedocs.io/en/latest/ "Chinese")**

**Offical [Docker Documents](https://docs.docker.com/get-started/overview/ "English")**

## **Image** ***vs*** **Container**
- Image:
    1. It is <span style="color: red;">read-only</span> file
    2. This file includs system, source code, files, dependency, tools
    3. It can be understood as a template
    4. Hierarchical concept

- Container:
    1. It is a running image
    2. Copy image and add a <span style="color: red;">read-write</span> layer (container layer)
    3. It can be created multiple containers by a image

## **VM** ***vs*** **Container**
- Container is not VM
    - Containers are just processes
    - The processes is limited to access to CPU memory resource
    - After processes stop, container will exit

![vm vs container!](vm_vs_container.png "graph 1")
## **IMAGE Acquisition**
- Pull from <span style="color: red;">registry</span> online
    - Public
    - Private
- Build from <span style="color: red;">Dockerfile</span> online
- Load from <span style="color: red;">file</span> online

![Image Acquisition!](image_acquisition.png "graph 2")


## **Dockerfile**
- Dockerfile constructs docker image
- Dockerfile includes commands
- Dockerfile has grammar rules

Example:
```
FROM ubuntu:21.04
RUN apt-get && \
DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -y python3.9-pip python3-pip python3.9-dev
ADD hello.py /
CMD ["python3", "/hello.py"]
```
Build it in the folder which has dockerfile and python file, **-t hello** is meaning tag the hello to latest version
> $ docker image build -t hello .

## **Check Out**
### **Environment** 
> $ docker info 

### **container log** 
> $ docker container logs ***CONTAINER ID***

dynamicly checking log:
> $ docker container logs ***CONTAINER ID*** -f

### **Container processes equal to system processes**
The commands for outside of container, The ***PID*** is different with inside of container:
> $ docker container top ***CONTAINER ID***

equal to

> $ ps aux | grep nginx

More detail for processes
> $ pstree -halps ***PID***

## **Pull Image**
Latest version
> $ docker image pull nginx

Specify version
> $ docker image pull nginx:1.20.0

## **Create Container**
> $ docker container run nginx

create an interacting container
> $ docker container run -it busybox sh

execute interacting command in a running container 
> $ docker container run -d nginx

> $ docker container exec -it ***CONTAINER ID*** sh

## **List Up**
### **image**
> $ docker image ls

### **Container**
old: 
> $ docker container ps -a

new:

> $ docker container ls -a

### **List all of containers ID**
> $ docker container ps -aq

## **Exit**
### **Container**
Exit one:
> $ docker container stop ***CONTAINER NAME*** or ***CONTAINER ID***

Exit in batches:
> $ docker container stop \$(docker container ps -qa)

## **Remove**
### **image**
In some situation it needs to remove container first then remove image
> $ docker image rm ***IMAGE NAME*** or ***IMAGE ID*** 

### **images or Containers in batches**
> $ docker container rm \$(docker container ps -qa)

### **Force to remove container when container is running**
> $ docker container rm ***CONTAINER ID*** -f 

## **Attached ***vs*** Detached**
attached mode is not using -d. detached mode is using -d:
> $ docker contianer run -d -p 80:80 nginx

Using attached mode
> $ docker attach ***CONTAINER ID***

**But not recommend to use attached mode because when press ctrl+c it will exit a container**

## **Save**
Save nginx:1.20.0 to nginx.image in local PC
> $ docker image save nginx:1.20.0 -o nginx.image

## **Load**
Load file and export to image 
> $ docker image load -i nginx.image

