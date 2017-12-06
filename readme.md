# docker-jenkins
Dockerized jenkins for Docker out of Docker (DooD)

Based on jenkins/jenkins:lts

Added libltdl7 to prevent this error:

```
docker: error while loading shared libraries: libltdl.so.7: cannot open shared object file: No such file or directory
```

# Requirement

You need to change the permission of docker.sock file, in order to give jenkins user inside the container access to host's docker

```
sudo chmod 0666 /var/run/docker.sock
```

# How to use

```
docker run -d --rm \
    -v `pwd`/jenkins_home:/var/jenkins_home \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v /usr/bin/docker:/usr/bin/docker \
    -p 8080:8080 \
    --name jenkins \
    hadigoh/jenkins:lts
```
