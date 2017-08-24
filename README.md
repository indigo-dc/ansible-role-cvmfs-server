Indigo-dc.cvmfs-server
=========================

Ansible role to install CernVM FS Server.

To Install CernVM FS Client: https://github.com/indigo-dc/ansible-role-cvmfs-client

To Create a CernVM Replica: https://github.com/mtangaro/ansible-role-cvmfs-replica (on-going)

This role has been create to be general, but it is used to create Galaxy Reference Data read-only repository. To populate Stratum Zero repository with Reference data: https://github.com/indigo-dc/Reference-data-galaxycloud-repository

### Development

- S3 support and squid proxy server support is on-going.
- Replica server support is on-going.

Requirements
------------
This ansible role is compatible with both CentOS 7 and Ubuntu 16.04 Xenial. 

The CernVM-FS (cvmfs) relies on OverlayFS or AUFS as default storage driver. Ubuntu 16.04 natively supports OverlayFS, therefore it is used as default, to create and populate the cvmfs server.

Python is required on host to run ansible: ``sudo apt-get install python``

The apt ansible module requires the following packages on host to run:

- python-apt (python 2)

Variables
---------
``repository_name``: set the cvmfs repository name (default: ``elixir-italy.galaxy.refdata``).

``stratum_zero``: set your domain or your ip address. (default: ``{{ ansible_default_ipv4.address }}``).

``repository_url``: set the cvmfs repository url (default: ``http://{{ stratum_zero }}/cvmfs/{{ repository_name }}``).

Example Playbook
----------------
The role is able to detect the server ip address automatically, through ansible. To customize your server, set your repository name.

```yaml
    - hosts: servers
      roles:
         - role: indigo-dc.cvmfs-server
```

License
-------
Apache Licence v2: http://www.apache.org/licenses/LICENSE-2.0

Reference
---------
Official cvmfs documentation: http://cvmfs.readthedocs.io/en/stable/cpt-repo.html

NIKHEF documentation: https://wiki.nikhef.nl/grid/Adding_a_new_cvmfs_repository

Author Information
------------------
Marco Tanagaro (ma.tangaro_at_ibiom.cnr.it)
