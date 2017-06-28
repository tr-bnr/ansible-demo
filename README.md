# Ansible Demo
An example of using ansible to setup a generic nginx installation on a virtual machine.

### Requirements
- [Ansible](http://docs.ansible.com/ansible/intro_installation.html#latest-releases-via-apt-ubuntu) `>=2.2.0`
- [Vagrant](https://www.vagrantup.com/docs/installation/)
- [Vagrant Host Manager](https://github.com/devopsgroup-io/vagrant-hostmanager)
- [VirtualBox](https://www.virtualbox.org/wiki/Linux_Downloads)

### Testing
- Launch the development VM `vagrant up dev-db`
- Run ansible playbook against the VM `ansible-playbook --inventory-file inventory main.yml`
- Navigate to [http://ansible-dev.pgh.com/](http://ansible-dev.pgh.com/)
- Verify you see the index page

