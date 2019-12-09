ansible_filebeat
=========

Ansible role to install filebeat with a simple configuration.


Role Variables
--------------

- version: filebeat version. (by default 7.5.0).
- processors: configuration of log handling . Path , tags and input type.
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
           processors:
             - paths: ['/var/log/httpd/*access.log']
               tags: ['httpd', 'access', 'isprime', '2.2']
               type: 'log'

             - paths: ['/var/log/httpd/*error.log', 'error_log']
               tags: ['httpd', 'error', '2.2']
               type: 'log'

             - host: 'localhost:5514'
               tags: ['httpd', 'error', '2.2']
               type: 'udp'

           elastic_hosts: ['https://ingest.mycluster.com:443']
           bulk_max_size: 50
