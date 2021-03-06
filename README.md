Role Name
=========

A role to deploy [Goacess](https://goacess.io) as a service with configuration.

Requirements
------------

None, but this only works for CentOS currently.

Role Variables
--------------

Destinations for various items

```
goaccess_base_dir:  /var/www/goaccess
goaccess_html_dir:  "{{ goaccess_base_dir }}/html"
goaccess_config:    "{{ goaccess_base_dir }}/goaccess.conf"
goaccess_systemd_service:   /etc/systemd/system/goaccess.service
```

Items relating to logs / http / http serving

```
goaccess_www_user:  apache
goaccess_www_group: apache
goaccess_apache_logs_dir:   /var/log/httpd
```

User for execution / service operation

```
goaccess_user_group_name:   goaccess
goaccess_user_group_gid:    null
goaccess_user_name:     goaccess
goaccess_user_home:     /var/opt/goaccess
goaccess_user_uid:      null
```

ALL other variables relate to templating the goaccess configuration. [Refer here for more information...](https://goaccess.io/man#configuration)

I tend to use a simple SSH forwarding with a static hostname to call the report
HTML served from 8080 on my VPS. I'm sure they're better ways, but it works...

```
Host staging-metrics
    LocalForward 8080 127.0.0.1:8080
    LocalForward 7890 127.0.0.1:7890
    Hostname staging-vps
```

Dependencies
------------

There are no role dependencies BUT goaccess 1.3 is the only version I've tested this against...

License
-------

MIT

Author Information
------------------

&copy; [Jim Circadian](https://github.com/JimCircadian) 2020

[Blog post available here](https://inconsistentrecords.co.uk/blog/deploying-analytics/)
