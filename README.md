# Centralized logging for CloudForms appliances using rsyslog.

The included Ansible playbook can be used to configure centralized logging for CloudForms logs.

## Requirements

### You need a host with Ansible installed to run the playbook from.

This can be one of the CloudForms appliances or another host which has SSH access to all of the appliances to be configured.

http://docs.ansible.com/ansible/intro_installation.html#latest-release-via-yum provides documentation for installing Ansible.

The following commands may be helpful:

```
subscription-manager repos --enable=rhel-7-server-optional-rpms --enable=rhel-7-server-extras-rpms
rpm -ihv https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
yum install ansible
```

### You'll need a copy of the code from the ansible directory here.

Clone or download a zip of this project.

### You'll need to add a disk to your central logging appliance.

The scripts expect a new disk to create a file system on under LVM control.  Based upon the default size of the CFME log file system of 10 GB, the size of this disk can be estimated at 10 GB times the number of CloudForms appliances that will log to this central log host.  You may want to add some extra for good measure and keep an eye on space consumption.

## Usage

* Review the ansible.cfg file and make updates if desired.
* Update the hosts files with your CloudForms appliances as described therein.
* Review and update the vars.yml file.
* From the cf_central_logging_rsyslog/ansible directory, run the Ansible playbook:

`ansible-playbook central_logging.yml`

Use at your own risk.
