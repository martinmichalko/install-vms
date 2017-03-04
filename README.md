## Create testing virtual environment

### Basics

tool to create set of testing virtual machines based on ansible playbooks and libguestfs virtualization library

used:
* kvm - for virtualization
* library libguestfs - for creation of vm's from prepared images
* openvirtual switch - for networking

system packages requirements (valid for debian8 probably also centos7):
openvswitch-switch curl libvirt-bin libguestfs-tools virtinst qemu-utils telnet
libguestfs-tools on debian8 should be installed from jessie backports

At the moment functional for vm's with centos and debian distributions (tested with debian-8 and centos-7.3).
You can list all possible operating systems versions with libguestfs
```bash
virt-builder --list
```

### Usage
Create the new directory for new project. Copy file inventory and host_vars/localhost.yml, update the values there and than you can install virtual environment with the command:
```bash
ansible-playbook -i inventory /path/to/playbook/files/create-update-config.yml --extra-vars "@host_vars/localhost.yml" --skip-tags "debug"
```