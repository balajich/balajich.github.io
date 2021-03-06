---
title: "Reverse proxy using Spring Cloud Gateway"
published: true
---
In this tutorial we are going to a run reverse proxy that is going to server requests on behalf of tomcat.
- Run reverse proxy (Spring Cloud Gateway Netty) on 8080 port
- Run rest api (tomcat) on 9090 port
- Modify the configurations of Netty to route requests to a newly added tomcat that is running on 9091
- How to handle tomcat fail overs
# Source Code
    git clone https://github.com/balajich/reverse-proxy-spring-cloud-gateway.git
# Architecture
![architecture](https://raw.githubusercontent.com/balajich/reverse-proxy-spring-cloud-gateway/master/architecture.png "architecture")
![proxy](https://raw.githubusercontent.com/balajich/reverse-proxy-spring-cloud-gateway/master/proxy.png "proxy")
# Video
[![Reverse proxy using Spring Cloud Gateway](https://img.youtube.com/vi/w-r-NO5Kqgk/0.jpg)](https://www.youtube.com/watch?v=w-r-NO5Kqgk)
# Prerequisite
- JDK 1.8 or above
- Apache Maven 3.6.3 or above
# Clean and Build
    mvn clean install
# Run Gateway server
     java -jar .\gateway\target\gateway-0.0.1-SNAPSHOT.jar
- The above command runs Netty  server on port 8080
- All the requests that are received on 8080 is forwarded to tomcat server running on 9090
# Run restapi server (tomcat)
    java -jar .\restapi\target\restapi-0.0.1-SNAPSHOT.jar
# Using curl to test environment
Access rest api via gateway

    curl http://localhost:8080/

Access rest api directly.

    curl http://localhost:9090/

# Run api server on 9091 port
     java '-Dserver.port=9091' -jar .\restapi\target\restapi-0.0.1-SNAPSHOT.jar
     
# Assignment
- Enhance gateway to route requests to tomcat running on 9091
- Observe requests are served in round robin fashion by the two servers running on 9090 and 9091
- Enhance gateway application to route requests to only healthy tomcats

# Solutions
Please refer next tutorial
    
    https://github.com/balajich/reverse-proxy-spring-cloud-gateway-enhanced-routing

