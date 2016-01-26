SickBeard
===========
This role deploys [SickBeard](http://sickbeard.com), a PVR for newsgroup users.

Requirements
------------
This role requires Ansible 2.0

Supported Platforms
-------------------
- Ubuntu: 15.04
- Debian: 8
- EL: 7

Role Variables
--------------
All variables have sensible defaults, which can be found in `defaults/main.yml`.
The current version includes the following variables:

| Name               | Default Value | Description                  |
|--------------------|---------------|------------------------------|
| `sickbeard_user_name`  | sickbeard | The user to run the SickBeard service |
| `sickbeard_group_name` | sickbeard | The primary group for `sickbeard_user_name` to run the SickBeard service |
| `sickbeard_user_uid` | 1005 | UID of the SickBeard service user |
| `sickbeard_group_gid` | 1005 | GID of the SickBeard service group |
| `sickbeard_user_home` | /var/lib/{{ sickbeard_user_name }} | home directory for the SickBeard service user |
| `sickbeard_conf_path` | {{ sickbeard_user_home }}/.sickbeard | Configuration directory for the SickBeard service |
| `sickbeard_library_path` | {{ sickbeard_user_home }}/data | Root library path, to be used for download directories, tv library etc. |
| `sickeard_port` | 4040 | The TCP port that the SickBeard web interface will bind to |
| `sickbeard_clone_uri` | 'git://github.com/midgetspy/Sick-Beard' | The remote Git repo to clone SickBeard from |
| `sickbeard_dependenceis` | - git-core | A list of dependency packages for SickBeard |
|                          | - python-cheetah |                                       |
| `sickbeard_service_file` | | |
| `    src`                  | sickbeard.service.j2 | The source template for the SickBeard service manifest |
| `    dest`                 | /etc/systemd/system/sickbeard.service | The destination to deploy the SickBeard service manifest to |
| `sickbeard_service_reload_command` | `systemctl daemon-reload` | The command to use when reloading the SickBeard service configuration |


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
