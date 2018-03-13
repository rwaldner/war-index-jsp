
# Simple WAR File with single index JSP file

## Build
```
$ ./gradlew war
```

## Deploy
### Tomcat 9
```
$ cd ~/Workspaces/war-index-jsp
$ docker run -it --rm -p 8888:8080 -v $(pwd)/build/libs:/usr/local/tomcat/webapps tomcat:9.0-jre8-alpine
```

### Tomcat 8.5
```
$ cd ~/Workspaces/war-index-jsp
$ docker run -it --rm -p 8888:8080 -v $(pwd)/build/libs:/usr/local/tomcat/webapps tomcat:8.5-jre8-alpine
```
### Tomcat 8.0
```
$ cd ~/Workspaces/war-index-jsp
$ docker run -it --rm -p 8888:8080 -v $(pwd)/build/libs:/usr/local/tomcat/webapps tomcat:8.0-jre8-alpine
```

### Tomcat 7
```
$ cd ~/Workspaces/war-index-jsp
$ docker run -it --rm -p 8888:8080 -v $(pwd)/build/libs:/usr/local/tomcat/webapps tomcat:7.0-jre8-alpine
```

### Jetty
```
$ cd ~/Workspaces/war-index-jsp
$ docker run -it --rm -p 8888:8080 -v $(pwd)/build/libs:/var/lib/jetty/webapps -d jetty:9.4.7-alpine
```

### Glassfish 5.0 nightly build
```
$ cd ~/Workspaces/war-index-jsp
# remove possible status files from a run before
$ ./gradlew clean war
$ docker run -it --rm -p 8888:8080 -v $(pwd)/build/libs:/glassfish5/glassfish/domains/domain1/autodeploy oracle/glassfish:nightly
```

### Glassfish 5.0
```
$ cd ~/Workspaces/war-index-jsp
# remove possible status files from a run before
$ ./gradlew clean war
$ docker run -it --rm -p 8888:8080 -v $(pwd)/build/libs:/glassfish5/glassfish/domains/domain1/autodeploy oracle/glassfish:5.0 
```

yields the following error message:
```
HTTP Status 500 - Internal Server Error

type Exception report
messageInternal Server Error
descriptionThe server encountered an internal error that prevented it from fulfilling this request.
exception
org.apache.jasper.JasperException: PWC6345: There is an error in invoking javac.  A full JDK (not just JRE) is required

note The full stack traces of the exception and its root causes are available in the GlassFish Server Open Source Edition 5.0 logs.
```

### Glassfish 4.1.2
```
$ cd ~/Workspaces/war-index-jsp
# remove possible status files from a run before
$ ./gradlew clean war
$ docker run -it --rm -p 8888:8080 -v $(pwd)/build/libs:/glassfish4/glassfish/domains/domain1/autodeploy oracle/glassfish:4.1.2
```


### Wildfly

```
$ cd ~/Workspaces/war-index-jsp
$ docker run -it --rm -p 8888:8080 -v $(pwd)/build/libs:/opt/jboss/wildfly/standalone/deployments/ jboss/wildfly
$ rm -f war-index-jsp.war.deployed
```

### Apache TomEE

### Apache Geronimo

### JOnAS
https://jonas.ow2.org

### Resin 

## View result
```
open -a Firefox http://localhost:8888/war-index-jsp/
```
