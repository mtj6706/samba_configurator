# samba_configurator
This is an ansible playbook and hosts file that will automatically configure samba on Ubuntu nodes
# NOTE:
- In order for this to run it is expected that the host node already has Samba installed on it. This is designed to automate the process of configuring Samba. Not the installation.
- The IP addresses of the blue-fileshares should be set in the /etc/hosts file of the controller like the following:
```
10.10.1.20 blue1-fileshare
10.10.2.20 blue2-fileshare
```
- This playbook requires the specification of the --ask-become-pass flag when run. There are several sudo level commands that are run as a part of this
- The team_num variable should be set under each hosts in the ansible/hosts file.
# Use
This ansible playbook configures a Samba server on the hosts listed under the bluefileshare group in the ansible/hosts file. This will:
1. Set the hostname to 'blue[1, 2]-fileshare'
2. Create the public fileshare /var/samba
3. Modify the publich share to be 777 perms
4. Modify the /etc/samba/smb.conf file to append the contents of smb_conf on the end
5. Restart the Samba service
6. Allow Samba traffic through firewall

# Example usage
