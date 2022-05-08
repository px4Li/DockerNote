# **Docker Notes**

**Offical [Docker Documents](https://docs.docker.com/get-started/overview/ "Docker Overview")**

## **Image** ***vs*** **Container**
- ### **image:**
1. It is <span style="color: red;">read-only</span> file
2. This file includs system, source code, files, dependency, tools
3. It can be understood as a template
4. Hierarchical concept

- ### **container:**
1. It is a running image
2. Copy image and add a <span style="color: red;">read-write</span> layer (container layer)
3. It can be created multiple containers by a image

## **Check Out**
### **Environment** 
> $ docker info 

### **container log** 
> $ docker container logs ***CONTAINER ID***

dynamicly checking log:
> $ docker container logs ***CONTAINER ID*** -f

### **Create Container**
ex:
> $ docker container run nginx

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

