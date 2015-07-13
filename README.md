#Docker Java 8

This repository contains the Dockerfile and support files to create a Debian / Java container.  This container only differs from the base image in that it exposes a VOLUME to run java software from the host.

##Base Docker Image
[java:8](https://github.com/docker-library/java/blob/fe489e584bd248f6ed6b379beed27eda755c5ba9/openjdk-8-jdk/Dockerfile)

##Installation

Install Docker.

Download automated build from public Docker Hub Registry: 
>docker pull enmobile/java:8

Alternatively, you can build an image directly from this repository: 
>docker build -t="enmobile/java:8" github.com/EnMobile/docker-java8

##Usage

>docker run -d -p 80:80 enmobile/java:8

##Customization

>docker run -d -p 8080:8080 -v \<path-to/local-java-jar\>:/app enmobile/java:8 java -jar /app/name-of-jar.jar 

where \<path-to/local-java-jar\> is an absolute path of a directory containing a jar file to execute, and 8080 should be changed to match the port your application exposes, if any.  If your java jar application does not expose a port, you may remove the -p option.

Mac boot2docker users will want to place the path to local jar directory under the automacially shared Users folder and should consider using something like:

>-v $(pwd)/build/libs:/app

After few seconds, open http://\<host\>:\<port\> to see your java application.
