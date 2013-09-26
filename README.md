My Ansible Playbooks
=================

This is just my repository of playbooks.

* create-user.yml
  * Creates a user with a password, a MySql DB, and an Apache virtual host.

### Setup Ansible

    sudo aptitude -y install git python-jinja2 python-yaml python-paramiko python-software-properties software-properties-common
    add-apt-repository ppa:rquillo/ansible
    aptitude update && aptitude install ansible
    echo "localhost" > /etc/ansible/hosts

You can now test by typing:

    ansible -c local -m ping all

You should see:

    localhost | success >> {
        "changed": false, 
        "ping": "pong"
    }

### Install passlib (for create-user.yml)

    wget https://passlib.googlecode.com/files/passlib-1.6.1.tar.gz
    tar -zxvf passlib-1.6.1.tar.gz
    cd passlib-1.6.1
    python setup.py install
   
### Run the play

By executing the following, it will setup only the commonly used components:

    ansible-playbook -c local --tags="common" ./create-user.yml
    
You can also just run the run-all script.
