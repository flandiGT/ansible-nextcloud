ansible-nextcloud
=================

Installs nextcloud as docker container.

System requirements
-------------------

* Docker
* Systemd

Role requirements
-----------------

* python-docker package

Tasks
-----

* Create volume paths for docker container
* Setup systemd unit file
* Start/Restart systemd service

Role parameters
--------------

| Variable      | Type | Mandatory? | Default | Description           |
|---------------|------|------------|---------|-----------------------|
| image_name    | text | no         | nextcloud | Docker image name    |
| image_version | text | no         | 13.0.0    | Docker image version |
| interface     | ip address | no   | 0.0.0.0          | Mapped network for web-interface ports |
| http_port     | port       | no   | 80               | Mapped HTTP port                       |
| data_volume   | path       | no   | <empty>          | Path to data volume                    |

Example Playbook
----------------

Usage (without parameters):

    - hosts: servers
      roles:
         - { role: install-docker-nextcloud }

Usage (with parameters):

    - hosts: servers
      roles:
      - role: install-docker-nextcloud
        http_port: 10081
        interface: "172.17.0.1"
        data_volume: /srv/docker/nextcloud
