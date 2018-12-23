# Comments on Provisioning Vagrant with Ansible (devops-sre-challenge) 


### Nginx.conf


#### Security

Best practices implemented:

- Nginx configured to proxy any traffic on port 80 to 443
- Disabled tls ver 1 - ssl_protocols TLSv1.1 TLSv1.2;
- Common recommended ciphers - ECDH+AESGCM:ECDH+AES256:ECDH+AES128:DH+3DES:!ADH:!AECDH:!MD5

### Certificates 

For clarity certs placed in dedicated directory - /etc/nginx/ssl/ 


### Ansible playbook


To maintain Idempodency runit is installed using the _get_url_ and _shell_ module. This should prevent package from being inadvertently reinstalled or updated since runit is dependent on 3rd party package.


#### Improvements

The playbook was designed to be readable, but could be shortened by defining variables and combining copy steps (cert, config files, etc) in one statement.
