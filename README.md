Running ansible playbook
------------------------

1. Run vagrant
	- $ Vagrant up

2. Get ip and add in localhost.ini

3. Running ansible-playbook
	- $ cd provisioning
	- $ ansible-playbook -i localhost.ini playbook.yml

Requirements
------------

- Vagrant 2.1.4
- ansible 2.6.4

