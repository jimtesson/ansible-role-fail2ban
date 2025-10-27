Setup requirements
=========

```
  pyenv install 3.12.0
  pyenv virtualenv 3.12.0 ansible-env
  pyenv activate ansible-env
  pip install --upgrade pip
  pip install -r requirements.txt
```

Fail2Ban
=========

Basic setup of fail2ban for sshd

Role Variables
--------------

You must specify the new user(s) details (name, pwd, authorized ssh key).

```
  fail2ban_maxretry: 3
  fail2ban_bantime: 86400 # 1 day
  # time window (in seconds) where the maxretry times should occur
  fail2ban_findtime: 3600 # 1 hour
  fail2ban_whitelist_all: '127.0.0.1'
```


Example
----------------

```
  - hosts: webservers
    tasks:
      - name: "Include fail2ban role"
        ansible.builtin.include_role:
          name: "jimtesson.fail2ban"
          vars:
            fail2ban_maxretry: 3
            fail2ban_bantime: 86400 # 1 day
            fail2ban_findtime: 3600 # 1 hour
            fail2ban_whitelist_all: '127.0.0.1' 

```


Tests
----------------

```
  # create the instance
  molecule create

  # apply the playbook
  molecule converge

  # test the playbook
  molecule verify

  # destroy the instance
  molecule destroy  
```

License
-------

BSD
