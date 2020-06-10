# Eureka! Clinical Admin Webapp
[Georgia Clinical and Translational Science Alliance (Georgia CTSA)](http://www.georgiactsa.org), [Emory University](http://www.emory.edu), 
Atlanta, GA

## What does it do?
It provides web pages for admin to manage user profiles and the user agreement. It also implements a proxy servlet and router 
for web clients to access the web services provided by eurekaclinical-user-service and eurekaclinical-user-agreement-service.

Latest release:[![Latest release](https://maven-badges.herokuapp.com/maven-central/org.eurekaclinical/eurekaclinical-admin-webapp/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.eurekaclinical/eurekaclinical-admin-webapp)

## Version 2.0
Updated dependencies.

## Version 1.1
Updated dependencies. Added route to eurekaclinical-protempa-service for future
job management functionality.

## Version 1.0
Initial release.

## Build requirements
* [Oracle Java JDK 8](http://www.oracle.com/technetwork/java/javase/overview/index.html)
* [Maven 3.2.5 or greater](https://maven.apache.org)

## Runtime requirements
* [Oracle Java JRE 8](http://www.oracle.com/technetwork/java/javase/overview/index.html)
* [Tomcat 7](https://tomcat.apache.org)
* Also running
  * The [eurekaclinical-user-service](https://github.com/eurekaclinical/eurekaclinical-user-service) war
  * The [eurekaclinical-user-agreement-service](https://github.com/eurekaclinical/eurekaclinical-user-agreement-service) war
  * The [cas-server](https://github.com/eurekaclinical/cas) war

## Proxied REST APIs
You can call all of [eurekaclinical-user-service](https://github.com/eurekaclinical/eurekaclinical-user-service)'s  and 
[eurekaclinical-user-agreement-service](https://github.com/eurekaclinical/eurekaclinical-user-agreement-service)'s
and 
[eurekaclinical-registry-service](https://github.com/eurekaclinical/eurekaclinical-registry-service)'s REST APIs through the proxy. 
Replace `/api/protected/` with `/proxy-resource`. The point of doing this is for web clients -- you can deploy the webapp on the 
same server as web client, and deploy the service on a separate server.

## Building it
The project uses the maven build tool. Typically, you build it by invoking `mvn clean install` at the command line. 
For simple file changes, not additions or deletions, you can usually use `mvn install`. 
See https://github.com/eurekaclinical/dev-wiki/wiki/Building-Eureka!-Clinical-projects for more details.

## Performing system tests
You can run this project in an embedded tomcat by executing `mvn process-resources cargo:run -Ptomcat` after you have built it. 
It will be accessible in your web browser at https://localhost:8443/eurekaclinical-admin-webapp/. Your username will be `superuser`.

## Installation
### Configuration
This webapp is configured using a properties file located at `/etc/ec-user/application.properties`. It supports the following 
properties:
* `eurekaclinical.adminwebapp.callbackserver`: https://hostname:port
* `eurekaclinical.adminwebapp.url`: https://hostname:port/eurekaclinical-admin-webapp
* `eurekaclinical.userservice.url`: https://hostname.of.userservice:port/eurekaclinical-user-service
* `eurekaclinical.useragreementservice.url`: https://hostname.of.useragreementservice:port/eurekaclinical-user-agreement-service
`eurekaclinical.registry.url`: https://hostname.of.registryservice:port/eurekaclinical-registry-service
* `cas.url`: https://hostname.of.casserver:port/cas-server
* `cas.url.login`: /login
* `cas.url.logout`: /logout
* `eurekaclinical.adminwebapp.allowedwebclients`: https://hostname.of.admin.webclient:port/eurekaclinical-admin-webclient/#/welcome/loggedIn

A Tomcat restart is required to detect any changes to the configuration file.

### WAR installation
1) Stop Tomcat.
2) Remove any old copies of the unpacked war from Tomcat's webapps directory.
3) Copy the warfile into the Tomcat webapps directory, renaming it to remove the version. For example, rename `eurekaclinical-admin-webapp-1.0.war` to `eurekaclinical-admin-webapp.war`.
4) Start Tomcat.

## Maven dependency
```
<dependency>
    <groupId>org.eurekaclinical</groupId>
    <artifactId>eurekaclinical-admin-webapp</artifactId>
    <version>version</version>
</dependency>
```

## Developer documentation
* [Javadoc for latest development release](http://javadoc.io/doc/org.eurekaclinical/eurekaclinical-admin-webapp) [![Javadocs](http://javadoc.io/badge/org.eurekaclinical/eurekaclinical-admin-webapp.svg)](http://javadoc.io/doc/org.eurekaclinical/eurekaclinical-admin-webapp)

## Getting help
Feel free to contact us at help@eurekaclinical.org.

