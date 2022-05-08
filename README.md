# **Docker Notes**

**Offical [Docker Documents](https://docs.docker.com/get-started/overview/ "Docker Overview")**

## **Image** ***vs*** **Container**
### **image:**
1. It is <span style="color: red;">read-only</span> file
2. This file includs system, source code, files, dependency, tools
3. It can be understood as a template
4. Hierarchical concept

### **container:**
1. It is a running image
2. Copy image and add a <span style="color: red;">read-write</span> layer (container layer)
3. It can be created multiple containers by a image

## **Check Version**
> $ docker version

## **Check Environment**
> $ docker info

## **Create Container**
ex:
> $ docker container run nginx
## **List image**
> $ docker image ls

## **Exit Container**
> $ docker container stop ***CONTAINER NAME*** or ***CONTAINER ID***
## **Remove image**
> $ docker image rm ***IMAGE NAME*** or ***IMAGE ID*** 
## **List Container**
old: 
> $ docker container ps -a

new:

> $ docker container ls -a
## **Check *log***
> $ docker logs -f
