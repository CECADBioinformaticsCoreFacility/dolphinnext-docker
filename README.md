DolphinNext docker version (CECAD)
========
DolphinNext original repository is located at https://github.com/UMMS-Biocore/dolphinnext.

For a quick start please check the quick start guide. 
https://dolphinnext.readthedocs.io/en/latest/dolphinNext/quick.html

DolphinNext can also be run as a standalone application using a docker container.
First docker image need to be build.
So, any change in the Dockerfile requires to build the image.

Build docker image
---------

1. To build docker image first clone one of the latest dolphinnext-docker

```
git clone https://github.com/CECADBioinformaticsCoreFacility/dolphinnext-docker.git
```

2. Build the image
```
cd dolphinnext-docker
docker build -t dolphinnext-docker .
```

Start the container
---------

1. We move database outside of the container to be able to keep the changes in the database everytime you start the container.
Please choose a directory in your machine to mount and replace `/path/to/mount` with your path. 
* Note: Please don't change the target directory(`/export`) in the docker image. 

```
mkdir -p /path/to/mount
```

2. While running the container;

```
docker run -m 10G -p 8080:80 -v /path/to/mount:/export -ti dolphinnext-docker /bin/bash
```

```
3. After you start the container, you need to start the mysql and apache server usign the command below;

```
startup
```

4. Verify that `dolphinnext` and `mysql` folders located inside of the `export` folder:

```
ls /export
```

5. Now, you can open your browser to access dolphinnext using the url below.

http://localhost:8080/dolphinnext

Hosting settings
------
We define `localhost:8080` in /path/to/mount/dolphinnext/config/.sec file and use that to log in or other operations.
You need to change `localhost` to the IP address or domain you use. 
Please update `BASE_PATH` and `PUBWEB_URL` as follows:

```
BASE_PATH = http://localhost:8080/dolphinnext
PUBWEB_URL = http://localhost:8080/dolphinnext/tmp/pub
```

to
```
BASE_PATH = http://your_temporary_domain_name:8080/dolphinnext
PUBWEB_URL = http://your_temporary_domain_name:8080/dolphinnext/tmp/pub
```
* Please don’t change other lines because others are used inside of docker.



 


