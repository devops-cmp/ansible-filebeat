ansible_filebeat
=========

Ansible role to install filebeat with a simple configuration.


Role Variables
--------------

- version: filebeat version. (by default 6.5.4)
- log_tags: List of tags to be added to the logs (by default [])
- elastic_hosts: List of elasticsearch ingress URLs.
- bulk_max_size: Max number of logs to be sent at the same time. (by default 50)
- paths: List of all the log paths to be sent. Wildcard is allowed.

Dependencies
------------

Systemd and centOS based Operative System.

Example Playbook
----------------

    - hosts: servers
      roles:
         -
           role: devops_cmp.ansible_filebeat
           version: 6.5.4
           log_tags: ['prod', 'myapp', 'mycomponent']
           elastic_hosts: ['https://ingest.mycluster.com:443']
           bulk_max_size: 200
           paths: ['/my/path/tologs/*']
