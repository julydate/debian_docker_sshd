# debian9_docker_sshd
Debian9 docker image with sshd

Simple Debian9 docker images with SSH access


## Usage

To create the image `debian9-ssh` with latest Debian release, 
execute the following commands on the debian9_docker_sshd folder:

    git checkout master
    docker build -t july/debian9-ssh . 

## Running debian9-ssh

To run a container from the image binding it to port 2333 in all interfaces, execute:

	docker run -d -p 2333:22 july/debian9-ssh

The first time that you run your container, a random password will be generated
for user `root`. To get the password, check the logs of the container by running:

	docker logs <CONTAINER_ID>

You will see an output like the following:

	========================================================================
	You can now connect to this debian9-ssh container via SSH using:

	    ssh -p <port> root@<host>
	and enter the root password 'qJixrU8ToNxe4xRg' when prompted

	Please remember to change the above password as soon as possible!
	========================================================================

In this case, `qJixrU8ToNxe4xRg` is the password allocated to the `root` user.

Done!


## Setting a specific password for the root account

If you want to use a preset password instead of a random generated one, you can
set the environment variable `ROOT_PASS` to your specific password when running the container:

	docker run -d -p 2333:22 -e ROOT_PASS="rootpasswd" july/debian9-ssh

