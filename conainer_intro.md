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
* container is a package or its a bundle which is  a combination of apps + application libarary + system depenededies (python , java so on )

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