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

The project's `container.yml` will be updated to include an *tomcat* service with the following port mappings, which you may wish to adjust:

```
ports:
  - 8005:8005
  - 8983:8983
  - 8443:8443
```

Role Variables
--------------

The following variables are defined in [defaults/main.yml](./defaults/main.yml), and can be set in `main.yml`:

TOMCAT_HOSTNAME
> Set the hostname (default localhost).

TOMCAT_HEAP_SIZE
> Set the heap size (default 256m).

Dependencies
------------

None.

License
-------

MIT/BSD

Author Information
------------------

[@awasilyev](https://github.com/awasilyev)
