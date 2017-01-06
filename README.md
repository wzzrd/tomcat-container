Tomcat 
======

[![Build Status](https://travis-ci.org/awasilyev/tomcat-container.svg?branch=master)](https://travis-ci.org/awasilyev/ansible-container)

Use this role to add an tomcat httpd service to your [Ansible Container](https://github.com/ansible/ansible-container) project. See Role Variables below for how to configure parameters. 

Run the following commands to install the service:

```
# Set the working directory to your Ansible Container project root
$ cd myproject

# Install the service
$ ansible-container install awasilyev.tomcat-container
```

Post Install
------------

### Connecting 
 
 In `container.yml` the Tomcat server port is mapped to host port **8080**. If you're using Docker Engine or Docker for Mac to run the service, connect to the web console at [http://localhost:8080](http://localhost:8080).

### Configuring
 
 On startup the *tomcat* container executes */usr/bin/entrypoint.sh* to set java heap size, and launch the Tomcat process. Any parameters passed to this script via the *command* directive in `container.yml` will be runned after JAVA_OPTS variable setting. By default it launches /usr/libexec/tomcat/server script.  

 The document root for the server is */var/lib/tomcat/webapps*. During image build, the list of paths defined using TOMCAT_ASSET_PATHS will be copied to the document root. During application development you will likely want to map a host path to the document root, which can be done by adding a `dev_overrides` section to the service:

```
dev_overrides:
   volumes:
     - ${PWD}/wars:/var/lib/tomcat/webapps
```


 See Environment Variables, and Role Variables below for details on setting java heap size and container hostname.
 

## Environment Variables

The following variables are defined in [defaults/main.yml](./defaults/main.yml), and can be set in `main.yml`:

TOMCAT_HOSTNAME
> Set the hostname (default localhost).

TOMCAT_HEAP_SIZE
> Set the heap size (default 256m).

TOMCAT_ASSET_PATHS
> Set the list of paths to be copied int /var/lib/tomcat/webapps (default ./apps)

## Dependencies
------------

None.

## License
-------

MIT/BSD

## Author Information
------------------

[@awasilyev](https://github.com/awasilyev)
