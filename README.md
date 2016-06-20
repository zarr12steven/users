user
=========


Role Variables
--------------

```
# List of group to management system group
#
# Template:
#   management_groups:
#     - name    :   devops      # Group name
#       gid     :   9527        # Group ID              (Default : null)
#       system  :   yes         # Is system group ?     (Default : no)
#       state   :   present     # Confirm installation  (Default : present)


# List of account to setup active users
#
# Template:
#   management_active_users:
#     nobody        :               # User name
#       password    :   random      # String        (Default : !!)
#       uid         :   98          # Set uid       (Default : None)
#       group       :   nobody
#       groups      :   adm,devops
#       full_name   :   Nobody
#       creaehome   :   yes
#       shell       :   /bin/bash
#       append      :   yes
#       state       :   present
#       public_key  :   nobody.pub              # File name     (Default : None)
#       remove_public_key   :  old_nobody.pub   # File name     (Default : None)


# Template:
#   management_remove_users:
#     - nobody      # It will remove home directory

```



Example Playbook
----------------

```
---
- hosts: servers
  roles:
    - role: user
      management_groups:
        - name: devopsk
          gid: 28
          system: yes
      management_active_users:
        nobody:
          full_name: Nobody
          groups:
            - ftp,adm
          public_key: nobody.pub
          remove_public_key: nobody_old_key.pub
      management_remove_users:
        - deploy
```


License
-------

BSD
