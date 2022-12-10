<img src="https://user-images.githubusercontent.com/92492605/201941889-f4a18508-506d-4b2e-bd12-ac9e4553c2b9.png" width="200" height="200" />

# ros-noetic
This is a test environment to allow Iceberg ASV members to get comfortable performing software development using Docker.

<!--Motive--> 
## Motive
When working on an embedded device (NVIDIA TX2) there are two challenges that our team faces for software development.
1. One computer = Development Bottleneck! 
2. Package and Dependency management
    - In our project there is **a lot** of 'stuff' that needs to be installed on our TX2. It can become difficult to manage the packages and drivers that are install on the device. This can result in the TX2 becoming bloated with unecessary software and it could become very hard to debug.

Docker helps solve both of these challenges. In our case, we are using Docker as a [virtual machine](https://www.redhat.com/en/topics/virtualization/what-is-a-virtual-machine) to emulate the same environment as the TX2. Docker will allow for any team member to develop in the same environment as the TX2 **remotely**. 

The Docker environment is built using a [Dockerfile](https://docs.docker.com/engine/reference/builder/) where all packages and depencies are listed. Installations in the Docker environment are not saved unless there are listed in the Dockerfile. The Dockerfile is used to document the installations on the TX2 and (most importantly) it allows for you to screw up without causing issues on the device! Any installations that are not recorded in the Dockerfile will not persist allowing for people to try things out and if it fails you can just restart the Docker environment.

## Workflow
All software is in source control (GitHub) and is written on your local machine. The software is then built and executed in the [Docker container](https://www.docker.com/resources/what-container/)

## References
[Robotic Sea Bass](https://roboticseabass.com/2021/04/21/docker-and-ros/) Docker/ROS workflow was heavily used in setting up Iceberg ASV's development environment.

If your not comfortable with Git, the linked website is a useful tool to sharpen your skills. [Git Resource](https://www.atlassian.com/git/tutorials/learn-git-with-bitbucket-cloud)

## Notes
- You **MUST** use a machine that uses an NVIDIA GPU or the Docker Container will **not** work.
- The tutorial is based on a ubuntu operating system. It will **not** work on Windows or MacOS.

# Get Started
<!--Docker install --> 
### Docker and Docker Desktop Install
It is necessary to install Docker and it is optional to install Docker Desktop. I would recommend installing Docker Desktop because the GUI makes it easier to manage and visualize all docker content on your machine.
- [Docker Installation](https://docs.docker.com/engine/install/ubuntu/)
- [Docker Desktop Installation](https://docs.docker.com/desktop/install/ubuntu/)
<!-- install git clone repo/ make a branch-->
### Git
1. [Git Installation] (https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
2. [SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
3. [Add SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
4. [Clone](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository) the **ros_noetic** repository
5. [Make a branch](https://www.atlassian.com/git/tutorials/using-branches/git-checkout) off of the main branch and use your **first name** as the name
<!-- Setup commands--> 
### Build Docker 
Click hyper-link if you would like to learn more about [docker build](https://docs.docker.com/engine/reference/commandline/build/). **NOTE** if changes are made to the Dockerfile, you must re-build the image to express the changes.
1. Enter directory that contains the docker file
    ```cd ros-noetic-docker/Docker/```
2. ```sudo docker build -t ros-noetic .```
### Run Docker Container
1. ```xhost +```
2. ```sudo docker run --name ros-noetic -it --net=host --env="DISPLAY" --env="QT_X11_NO_MITSHM=1" --volume="/tmp/.X11-unix:/tmp.X11-unix:rw" --volume="/home/ros-noetic-docker/catkin_ws:/ws" ros-noetic```
3. Check the container is running
    - Enter new terminal
    - ```sudo docker container ls```
    - You should see the container listed
    ![image](https://user-images.githubusercontent.com/92492605/206874844-6b9855a8-5b29-4aa3-bd4d-e69eab89a3b3.png)
    
### First time using container
1. Run build catkin environment
    - In docker container:
        - ```cd ws```
        - ```catkin_make```



<!-- Docker Run Command-->
<!-- Docker container exec -->
<!--Useful Docker Commands --> 
<!--Notes about Docker --> 
