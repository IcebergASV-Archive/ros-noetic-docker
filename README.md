<img src="https://user-images.githubusercontent.com/92492605/201941889-f4a18508-506d-4b2e-bd12-ac9e4553c2b9.png" width="200" height="200" />

# ros-noetic
This is a test environment to allow Iceberg ASV members to get comfortable performing software development using Docker.

# Get Started
<!--Motive--> 
## Motive
When working on an embedded device (NVIDIA TX2) there are two challenges that our team faces for software development.
1. One computer = Development Bottleneck! 
2. Package and Dependency management
    - In our project there is **a lot** of 'stuff' that needs to be installed on our TX2. It can become difficult to manage the packages and drivers that are install on the device. This can result in the TX2 becoming bloated with unecessary software and it could become very hard to debug.

Docker helps solve both of these challenges. In our case, we are using Docker as a [virtual machine](https://www.redhat.com/en/topics/virtualization/what-is-a-virtual-machine) to emulate the same environment as the TX2. Docker will allow for any team member to develop in the same environment as the TX2 **remotely**. 

The Docker environment is built using a [Dockerfile](https://docs.docker.com/engine/reference/builder/) where all packages and depencies are listed. Installations in the Docker environment are not saved unless there are listed in the Dockerfile. The Dockerfile is used to document the installations on the TX2 and (most importantly) it allows for you to screw up without causing issues on the device! Any installations that are not recorded in the Dockerfile will not persist allowing for people to try things out and if it fails you can just restart the Docker environment.
<!--Docker install --> 
<!--Docker Hub install -->
<!-- install git clone repo/ make a branch-->
<!-- Setup commands--> 
<!-- Docker Run Command-->
<!-- Docker container exec -->
<!--Useful Docker Commands --> 
<!--Notes about Docker --> 
