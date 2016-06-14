
williamyeh.uwsgi for Ansible Galaxy
============


## Summary

Role name in Ansible Galaxy: **[williamyeh.uwsgi](https://galaxy.ansible.com/williamyeh/uwsgi/)**

This Ansible role has the following features for uWSGI:

 - Install specific version.
 - No configuration (*real* configuration should be left to user's template files; see **Usage** section below).




## Role Variables

### Mandatory variables

None.


### Optional variables

User-configurable defaults:

```yaml
uwsgi_version
```

For example:

```yaml
# specific version
uwsgi_version: 2.0.13.1
```



## Handlers

- `restart uwsgi`

- `reload uwsgi`

- `stop uwsgi`



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
  become: true
  roles:
    - williamyeh.uwsgi
```


### Step 3: copy user's config files, if necessary


More practical example:

```yaml
---
# file: complex-playbook.yml

- hosts: all
  become: true
  roles:
    - williamyeh.uwsgi

  vars:
    uwsgi_version: 2.0.13.1

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

  - [theonion.uwsgi-emperor](https://galaxy.ansible.com/theonion/uwsgi-emperor/)
  - [gdamjan.uwsgi](https://galaxy.ansible.com/gdamjan/uwsgi/)

Also, the handling of pip was borrowed from:

  - [gmacon's folk of ansible-pip](https://github.com/gmacon/ansible-pip/blob/variable_executables/tasks/main.yml)

