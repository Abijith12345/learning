 # docker
 we are gonna learn somthing on docker.
### Virtual machine
when we deling with 1000 of sysetem, in this plce hyperwiser will use.
hypervisor is used the concept of virtualization. Hypervisor will  be on top of an phydical server,  using that it will create an virtual machine


### Why we moving towards container?

<p>we can save some money by moving the physical server to vitutalmachine</p>
<p>But in case we are not using the full capacity we are wasting the resources. we are paying for that as well.</p>
<p>Container is an advancement of virtual machine.</p>
<p>To solve this problem container has been found.</p>
<p>compare to container the VM is more secure, because the VM have the full control that is fully <p>isolated, but in the case of container  it doesn't have complete OS. There is logical isolation  <p>for conatiner but that is not fully isolated.</p>

<p>container can be created in 2 ways</p>

* Container on top of VM - In a virtual machine on container will run on contanierzation platform like docker.
* Container on top of Physical server - in a  physical server use of hypervisor create an VM   - on top of os containerizatoin platform ex: Docker ->container will run.

### Container  characteristics
* containers are light weight in nature, it is easy to transfer.
* container doesn't have an  complete opeating system, they use the resourse form VM or physical server that they are running on.
* resourse will share from  the host OS
* container have a minimal os they have a base image
* A container is a bundle of Application, Application libraries required to run your application and the minimum system dependencies.(python , java so on )

## Docker

* for symblifiying the containeraization  method  Docker came up, with the help of docker, we can easliy  write a docker file -> and make this an image -> and use the image and run the container, these all are controlled by docker engine 

* In case docker engine is down , all the container will down. because is an singale point of Failurw (SPF)
* so for this issue *Builda* came up,  we can use the Builda commends , we can use the shell scipt,  it also support docker image.

### Files and Folders in containers base images

```
    /bin: contains binary executable files, such as the ls, cp, and ps commands.

    /sbin: contains system binary executable files, such as the init and shutdown commands.

    /etc: contains configuration files for various system services.

    /lib: contains library files that are used by the binary executables.

    /usr: contains user-related files and utilities, such as applications, libraries, and documentation.

    /var: contains variable data, such as log files, spool files, and temporary files.

    /root: is the home directory of the root user.
```



### Files and Folders that containers use from host operating system

```
    The host's file system: Docker containers can access the host file system using bind mounts, which allow the container to read and write files in the host file system.

    Networking stack: The host's networking stack is used to provide network connectivity to the container. Docker containers can be connected to the host's network directly or through a virtual network.

    System calls: The host's kernel handles system calls from the container, which is how the container accesses the host's resources, such as CPU, memory, and I/O.

    Namespaces: Docker containers use Linux namespaces to create isolated environments for the container's processes. Namespaces provide isolation for resources such as the file system, process ID, and network.

    Control groups (cgroups): Docker containers use cgroups to limit and control the amount of resources, such as CPU, memory, and I/O, that a container can access.
    
```

It's important to note that while a container uses resources from the host operating system, it is still isolated from the host and other containers, so changes to the container do not affect the host or other containers.

**Note:** There are multiple ways to reduce your VM image size as well, but I am just talking about the default for easy comparision and understanding.


* docker build to buld a container
* docker run to run a docekr container on our machine
* docker push -> push the container to docker registry
* docker pull -> anybidy in the world can download and use it.



## Most common use case of docker in between developers and QA egnineer

* Before without container what they do is , dev will develop a code and tester will downloaad the app from repo and test, in this cse there will be a lot of dependencies will be there to run an application

* but after the innovation of docker, the stester can  easily pull the image and run that no need to worry about is it a  mac or windows or linux,, or needed any system dependencies

## what is the part of thing in  contaneraize an application.

* we need to create an docker file for that
* in the docekr file should have the base OS ex: FROM ubutnu, FROM python
* and we need to mention the work directory using ex: WORKDIR </app>
* we need to copy the source code - COPY <file name>
* we need to install the requiremnt that needed to run the app - using the specific command that support the os
* ENTRYPOINT - it can't be changeable ex: ENTRYPOINT ["python 3"]
* CMD - it can be changeable  ex: CMD ["manage.py", "runserver", "0.0.0.0:8000"]  
* from the above example if any people try to run  this application and, their machine alreaday have occuiped the port 8000 with other app, then it wont be executblae, so since it is in cmd  can change that ans use that, but in case of entry point we can't do that


## Multistage docker

* To build an docker we should select an base image such as linux, mac, or someting, that make the image size ti high
* So solve this problem multistage docker file has been introduced, with the use of distroless image we can able to easily run our container.
* distroless imae - it is used to run time only. ex: python it is using only for the python app, so we can't run even the basic shell command
* we will use the dependencied of the base image using the alias  : (ex ): FROM ubuntu AS build
* build is in an alias  for the abobe example.


# Docker BIND MOUNDS and volume

* BIND MOUNDS  - allow to bind directory to container, by using this even the container goes down, we can use the information from this information. so we can easily bind this Directory with new container and we can continue use that.
* Bind mounds are binded to the container by using the directory location so it restricted to single host where the container running
* Volumes - By using the Docker CLI create an logical isolated volume in our host, we can use that like bindmounts, we can destroy,or we can use that with another container.
* advantage of volume is we are not restricted to a single host we can create the volume from several places such as another ec2 instance, s3, NFS so and so
* we can control all this by docker CLI, and also it was high performance, because it was not on the host we use.



## Working with Volumes

* docker Volume create <Volume name>  - Tpo create new volume 
* docket volume ls - To see the list of Volumes
* dokcer volume inspect < volume name >  - to see the deatils of specific volume
* docker  volume rm <volume  name> - To remove the volume
* docker ps - to see the list of running containers
* docker inspect <docker name> - to see the docker details

* we cant delete a volume directly , we need to stop the container and need to delete the container , then only it is possible

* so concept of the volume is even a containers goes down the details will be on the volume so we can, use it on the another container , there wont be any information lost.
