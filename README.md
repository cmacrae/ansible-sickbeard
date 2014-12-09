SickBeard
===========
This role deploys [SickBeard](http://sickbeard.com), a PVR for newsgroup users.

Requirements
------------
This role has been written with [SmartOS](https://smartos.org) in mind, and is designed to be deployed to a [zone](https://wiki.smartos.org/display/DOC/Zones), for use as a server.
However, if popular demand shows, I'll happily add in support for other operating systems.

Role Variables
--------------
All variables have sensible defaults, which can be found in `defaults/main.yml`.
The current version includes the following variables:

| Name               | Default Value | Description                  |
|--------------------|---------------|------------------------------|
| sickbeard_user_name  | sickbeard | username to run the SickBeard service |
| sickbeard_group_name | sickbeard | groupname to run the SickBeard service |
| sickbeard_user_uid | 1000 | UID of the SickBeard service user |
| sickbeard_group_gid | 1000 | GID of the SickBeard service group |
| sickbeard_user_home | /opt/{{ sickbeard_user_name }} | home directory for the SickBeard service user |
| sickbeard_conf_path | {{ sickbeard_user_home }}/.sickbeard | configuration directory for the SickBeard service |
| sickbeard_library_path | {{ sickbeard_user_home }}/data | root library path, to be used for download directories, tv library etc. |
| sickbeard_binary_path | {{ sickbeard_user_home }}/bin/Sick-Beard | path where the SickBeard source will reside |
| sickeard_oirt }} | 4040 | the TCP port that the SickBeard web interface will bind to |
| sickbeard_pid_file | {{ sickbeard_conf_path }}/sickbeard.pid | pidfile for the SickBeard service to write the pid to |
| sickbeard_path_var | /opt/local/bin:/opt/local/sbin:/usr/bin:/bin | set $PATH for the SickBeard service script |
| sickbeard_service_args | --config {{ sickbeard_conf_path }}/config.ini<br> --daemon --pidfile={{ sickbeard_pid_file }}<br> -p {{ sickbeard_port }}
 | arguments the SickBeard service will use when starting |

Example Playbook
----------------

    - hosts: sickbeard_servers
      roles:
        - role: cmacrae.sickbeard

Or, passing parameter values:

	- hosts: sickbeard_servers
	  roles:
	    - { role: cmacrae.sickbeard, sickbeard_user_name: downld, sickbeard_group_name: downld }
License
-------
MIT

Author Information
------------------
Created by [Calum MacRae](http://cmacr.ae)

Feel free to:  
Contact me - [@calumacrae](https://twitter.com/calumacrae), [mailto:calum0macrae@gmail.com](calum0macrae@gmail.com)  
[Raise an issue](https://github.com/cmacrae/ansible-sickbeard/issues)  
[Contribute](https://github.com/cmacrae/ansible-sickbeard/pulls)  
