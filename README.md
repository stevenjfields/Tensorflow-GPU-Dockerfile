# Tensorflow GPU Docker Image
I took the example dockerfile given by the tensorflow team and modified it (_very slightly_) for my liking. 
I really only changed it from jupyter to jupyter lab and erased some lines that downloaded tutorial notebooks.
You can find the original [Dockerfile here](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/tools/dockerfiles/dockerfiles)
and the bashrc file is [here](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/tools/dockerfiles). This was all done on Ubuntu 20.04 so all the instructions will target that OS. This was really just created for my own use but I figured I'd make it public if anyone else wants to use it.

# Installing Docker
- First make sure you have docker installed, you can find instructions [here](https://docs.docker.com/engine/install/ubuntu/).
- Next follow [these instructions](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker) to install the nvidia container toolkit. This will let docker utilize nvidia GPUs.
- You also need to have docker-compose installed, so here are [instructions for that as well](https://docs.docker.com/compose/install/)

# Running
In order to run type `docker-compose up` into the command line in this directory. It will spin up the container and sync all notebooks created to the `Notebooks` folder, as well as install all packages mentioned in the pyproject.toml file.

# Package Management
I add poetry to the dockerfile to manage packages outside of the ones included in the original Dockerfile. It defaults to only include the original dockerfile packages, pandas, and seaborn. Any others can be added inside of jupyter lab. Create a new window, select terminal as the type, and enter `poetry add <package_name>`.
