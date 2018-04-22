Ansible NGINX Role
==================

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-bluestar.nginx-5bbdbf.svg)](https://galaxy.ansible.com/bluestar/nginx)
[![Build Status](https://travis-ci.org/bluestar/ansible-role-nginx.svg?branch=master)](https://travis-ci.org/bluestar/ansible-role-nginx)

__Important: This is a fork of [nginxinc.nginx role](https://galaxy.ansible.com/nginxinc/nginx/).__ 

The function of the role is to install NGINX Open Source on your target host with defaults different from the original role.

Requirements
------------

This role was developed using Ansible 2.5.0. Backwards compatibility is not guaranteed.

Use `ansible-galaxy install bluestar.nginx` to install the role on your system.

This role was only tested on CentOS 7. It may work on other systems, supported by NGINX [NGINX Open Source](https://nginx.org/en/linux_packages.html#mainline).

Role Variables
--------------

This role has multiple variables. The defaults for all these variables are the following:

    ---
    # Specify which branch of NGINX Open Source you want to install.
    # Options are 'mainline' or 'stable'.
    # Default is mainline.
    branch: mainline

    # Install nginscript, perl, geoip, image-filter, rtmp and/or xslt modules.
    # Default is false.
    modules:
      njs: false
      perl: false
      geoip: false
      image_filter: false
      rtmp: false
      xslt: false

    # Enable NGINX status data.
    # Will enable 'stub_status' in NGINX Open Source and 'status' in NGINX Plus.
    # Default is true.
    status_enable: true

    # Enable uploading NGINX configuration files to your system.
    # Default for uploading files is false.
    # Default location of files is the files folder within the NGINX Ansible role.
    main_push_enable: false
    main_push_location: conf/nginx.conf
    http_push_enable: false
    http_push_location: conf/http/*.conf
    stream_push_enable: false
    stream_push_location: conf/stream/*.conf

    # Configuration variables to create a templated NGINX configuration.
    # Defaults are the values found in a fresh NGINX installation.
    main_template_enable: false
    main_template_user: nginx
    main_template_worker_processes: auto
    main_template_error_level: warn
    main_template_worker_connections: 1024
    http_template_enable: false
    http_template_keepalive_timeout: 65
    http_template_listen: 80
    http_template_server_name: localhost
    stream_template_enable: false
    stream_template_listen: 12345

Dependencies
------------

None

Example Playbook
----------------

This is a sample playbook file for deploying the Ansible Galaxy NGINX role in a localhost and installing the open source version of NGINX.

    ---
    - hosts: localhost
      become: true
      roles:
        - role: bluestar.nginx

This is a sample playbook file for deploying the Ansible Galaxy NGINX role to a dynamic inventory containing the `nginx` tag.

    ---
    - hosts: tag_nginx
      remote_user: root
      roles:
        - role: bluestar.nginx

To run any of the above sample playbooks create a `setup-nginx.yml` file and paste the contents. Executing the Ansible Playbook is then as simple as executing `ansible-playbook setup-nginx.yml`.

Alternatively, you can also clone this repository instead of installing it from Ansible Galaxy. If you decide to do so, replace the role variable in the previous sample playbooks from `bluestar.nginx` to `ansible-role-nginx`.

License
-------

[Apache License, Version 2.0](https://github.com/bluestar/ansible-role-nginx/blob/master/LICENSE)

Author Information
------------------

1. Alessandro Fael Garcia
1. [NGINX Inc](https://www.nginx.com/)
1. Mikhail Krivoshein
