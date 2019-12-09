ansible_filebeat
=========

Ansible role to install filebeat with a simple configuration.


Role Variables
--------------

- version: filebeat version. (by default 7.5.0).
- pipelinematch: List of tags and list of paths to be parsed by filebeat. Wildcard is allowed.
- elastic_hosts: List of elasticsearch ingress URLs.
- bulk_max_size: Max number of logs to be sent at the same time. (by default 50)

Dependencies
------------

Systemd and centOS based Operative System.

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: devops_cmp.ansible_filebeat
           version: 7.5.0
           pipelinematch:
             tags:
             - ["httpd","httpd-error"]
             paths:
             - ["/var/log/httpd","/var/log/httpd/*error*"]

           elastic_hosts: ['https://ingest.mycluster.com:443']
           bulk_max_size: 50
