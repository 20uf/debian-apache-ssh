apache-master-ssh
============

Simple ubuntu apache docker images with SSH access

![enter image description here](https://circleci.com/gh/20uf/apache-master-ssh.svg?style=shield&circle-token=:circle-token)

Usage
-----

To create the image `apache-master-ssh` with lasted ubuntu release, 
execute the following commands on the apache-master-ssh folder:

    git checkout master
    docker build -t 20uf/apache-master-ssh

Running debian-ssh
--------------------

To run a container from the image binding it to port 2222 in all interfaces, execute:

	docker run -d -p 2222:22 20uf/apache-master-ssh

The first time that you run your container, a random password will be generated
for user `root`. To get the password, check the logs of the container by running:

	docker logs <CONTAINER_ID>

You will see an output like the following:

	========================================================================
	You can now connect to this debian-ssh container via SSH using:

	    ssh -p <port> root@<host>
	and enter the root password 'UCr7W3U0iSGV' when prompted

	Please remember to change the above password as soon as possible!
	========================================================================

In this case, `UCr7W3U0iSGV` is the password allocated to the `root` user.

Done!


Setting a specific password for the root account
------------------------------------------------

If you want to use a preset password instead of a random generated one, you can
set the environment variable `ROOT_PASS` to your specific password when running the container:

	docker run -d -p 2222:22 -e ROOT_PASS="mypass" 2222:22 20uf/apache-master-ssh

