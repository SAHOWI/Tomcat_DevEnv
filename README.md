# Tomcat Dev Env

This example is using the Tomcat Docker image from https://hub.docker.com/_/tomcat?tab=description

## Get the Docker Image
```powershell
PS C:\> docker pull tomcat
```
## Use the Tomcat Docker Image

### Start the Tomcat Server
```powershell
PS C:\> docker run -it --rm -p 8888:8080 tomcat:9.0
```

You can connect now on your local host machine to your Tomcat with http://localhost:8888
This will show a 404 response, as per security reasons the webapps directory is empty.
If you need the sample apps, they are located in webapps.dist.
You may copy them to from webapps.dist to webapps - but don't forget:
This is a container, changes will not be written back to the image the container been started from!
The next time you stop the container, all changes are lost (this is the benefit of a container!)


### Connect to running Container
```powershell
PS C:\> docker ps
CONTAINER ID   IMAGE        COMMAND             CREATED         STATUS         PORTS                                       NAMES
40bbfaf7d0d2   tomcat:9.0   "catalina.sh run"   6 minutes ago   Up 6 minutes   0.0.0.0:8888->8080/tcp, :::8888->8080/tcp   reverent_goldwasser
PS C:\> docker exec -it 40bbfaf7d0d2 /bin/bash
root@40bbfaf7d0d2:/usr/local/tomcat#

```

