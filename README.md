Setup requirements
=========

```
  pyenv install 3.12.0
  pyenv virtualenv 3.12.0 ansible-env
  pyenv activate ansible-env
  pip install --upgrade pip
  pip install -r requirements.txt
```

Run tests on local vagrant instance
=========

  ## Run local vm @192.168.56.30
    git clone git@github.com:jimtesson/vagrant-vm-for-tests.git
    cd vagrant-vm-for-tests
    vagrant up ionosVps

  ## Run ansible
    ssh-keygen -f ~/.ssh/known_hosts -R 192.168.56.30
    ansible -i ./inventory/hosts-tests.yml ionos_vps_test -m ping
    ansible-playbook -i ./inventory/hosts.yml ./main.yml -l testing

Prod provisionning
=========

    ansible-playbook -i ./inventory/hosts.yml ./main.yml -l prod