
williamyeh.uwsgi for Ansible Galaxy
============


## Summary

Role name in Ansible Galaxy: **[williamyeh.uwsgi](https://galaxy.ansible.com/list#/roles/2262)**

This Ansible role has the following features for uWSGI:

 - Install specific version.
 - No configuration (*real* configuration should be left to user's template files; see **Usage** section below).




## Role Variables

### Mandatory variables

Variables needed to be defined in user's playbook:

```yaml
uwsgi_version
```

For example:

```yaml
# specific version
uwsgi_version: 2.0.8


# don't care version
uwsgi_version: ~
```



### Optional variables

User-configurable defaults: None.




## Usage


### Step 1: add role

Add role name `williamyeh.uwsgi` to your playbook file.


### Step 2: add variables

Set vars in your playbook file.

Simple example:

```yaml
---
# file: simple-playbook.yml

- hosts: all

  roles:
    - williamyeh.uwsgi

  vars:
    uwsgi_version: 2.0.8
```


### Step 3: copy user's config files, if necessary


More practical example:

```yaml
---
# file: complex-playbook.yml

- hosts: all

  roles:
    - williamyeh.uwsgi

  vars:
    uwsgi_version: 2.0.8

  tasks:
    - name: Copy project-specific config file(s) for uWSGI 
      template: src=templates/app-1.ini.j2  dest=/etc/uwsgi/vassals/app-1.ini
      template: src=templates/app-2.ini.j2  dest=/etc/uwsgi/vassals/app-2.ini
```


## Dependencies

None.


## License

Licensed under the MIT License. See the [LICENSE file](LICENSE) for details.


## History

Some roles on Ansible Galaxy inspired me:

  - [theonion.uwsgi-emperor](https://galaxy.ansible.com/list#/roles/1917)
  - [gdamjan.uwsgi](https://galaxy.ansible.com/list#/roles/90)

Also, the handling of pip was borrowed from:

  - [gmacon's folk of ansible-pip](https://github.com/gmacon/ansible-pip/blob/variable_executables/tasks/main.yml)

