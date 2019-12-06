User Management
=========

This role create User and Groups on target machine.


Role Variables
--------------

This role required below variables to be supply in order to created user or group or both.

Required Variables To Create User:

  1. userName        ( **Note:** Name of the User to be created.)
  2. userPWD.        ( **Note:** User Password. It will be hash and won't be writting to any logs.)
  3. userGroups      ( **Note:** Name of the group user need to be added. User `,` separators for multiple groups)    
  4. userHomedic     ( **Note:** User `yes` or `no`. Yes will created home directory and no will not.)

Required Varaibles To Create Group:

  1. inputGroup.     ( **Note:** Name of the group to be created.)

Things To Know
----------------
By default, it will created User and Group. But, if you want to create only User or Group. Turn off the flag for User or Group.

```
group_create: False

or 

user_create: False
```

Running Playbook
----------------

You can run playbook from you local machine or call role from other role.

Create Both User & Group
```
ansible-playbook -i 'inventoryfilename' --extra-vars="ansible_user=loginusername inputGroup=demo userName=demouser userPWD='userpassword' userGroups=demo userHomedic=yes" user_management/run-user-management.yml
```
Create Only User

```
ansible-playbook -i 'inventoryfilename' --extra-vars="ansible_user=loginusername userName=demouser userPWD='$1$H/2ABHKm$Ljc84T6n79yq4z6boWp0O/' userGroups=demo userHomedic=yes group_create=False" user_management/run-user-management.yml
```

Create only Group
```
ansible-playbook -i 'inventoryfilename' --extra-vars="ansible_user=loginusername inputGroup=demo user_create=False"  user_management/run-user-management.yml
```

**Note:** When Running from local machine make sure you run from outside `user_management` folder otherwise it will say role not found.

