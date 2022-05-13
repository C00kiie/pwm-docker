# pwm-docker

This docker-composer image includes:
- pwm-manager/pwm
- openldap
- phpldapmanager

all those applications will fall into one network called `pwm-network` 


# installation process
- enter ldap server wiht `docker exec -it openldap /bin/bash` and execute admin_user `ldif` file
- run `ldapmodify -H ldapi:// -Y EXTERNAL` and enter the contents of `permissions.ldif`
- run `docker network inspect pwm-instance` to check the IPs of each component
- enter pwm-manager instance on port 8443, and go through the setup processes
- make sure to write the IP/Hostname correctly, setting port to 389 and with non-tls
- the pwm-proxy account is `cn=pwmproxyp,ou=people,dc=example,dc=org` and password is `123`, make sure to change it prior to installtion
- the organizationl unit is `ou=people,dc=example,dc=org`
- the administrative account is the same user as the pwmproxyp
- the rest of the setup process is a simple processes which can be gone through with simple "next" clicks

and you are done and ready to go!

#Notes
- the data are persistent inside docker volumes
- make sure to make the necessary changes for admin password in docker-compose and inside `ldif` files
- post-installation, everything should be mapped by nginx and not directly exposed by docker-compose



