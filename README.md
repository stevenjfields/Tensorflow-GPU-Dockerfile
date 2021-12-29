# Tensorflow GPU Docker Image
I took the example dockerfile given by the tensorflow team and modified it (_very slightly_) for my liking. 
I really only changed it from jupyter to jupyter lab and erased some lines that downloaded tutorial notebooks.
You can find the original [Dockerfile here](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/tools/dockerfiles/dockerfiles)
and the bashrc file is [here](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/tools/dockerfiles). This was all done on Ubuntu 20.04 so all the instructions will target that OS. This was really just created for my own use but I figured I'd make it public if anyone else wants to use it.

# Building
- First make sure you have docker installed, you can find instructions [here](https://docs.docker.com/engine/install/ubuntu/).
- Next follow [these instructions](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker) to install the nvidia container toolkit. This will let docker utilize nvidia GPUs.
- Finally build the image by running the command `docker build -t tf270 .` inside this folder.
    - If you change the tensorflow version it might make sense to change the name from `tf270`. The dockerfile currently targets tensorflow version `2.7.0` though.

# Running
Running is made pretty easy, just type `./start.sh` into the command line. It will spin up the container and sync all notebooks created to the `Notebooks` folder.
- **Note:** if you changed the name of the container as mentioned above you will need to make that same change inside the start.sh file.
- If `./start.sh` doesn't work immediately try changing permissions with `sudo chmod +x start.sh`