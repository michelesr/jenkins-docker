# Docker container for Jenkins

Docker Container for Jenkins CI with `sudo` and `docker-compose`.

An example of usage:
    
    docker run --name gogs -d \
             -p 3000:3000 \
             -p 5000:8080 \
             -v $HOME/gogs_data:/data \
             codeskyblue/docker-gogs

    docker run --name jenkins -d \
         -v /var/run/docker.sock:/var/run/docker.sock \
         -v /usr/lib/libdevmapper.so.1.02:/usr/lib/libdevmapper.so.1.02 \
         -v $(which docker):/usr/bin/docker \
         -v $HOME/jenkins_data:/var/jenkins_home \
         --net container:gogs \
         michelesr/jenkins
