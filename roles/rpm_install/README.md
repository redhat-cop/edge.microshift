Role Name
=========

This role automates installing and initial configuration of [Microshift](https://microshift.io/) on a rpm based system.

Requirements
------------

None

Role Variables
--------------

## rpm_install_pull_secret

Type: string
Required: true

Example:

```yaml
rpm_install_pull_secret: "{{ lookup('file', '~/Downloads/pull-secret.txt') }}"
```

## rpm_install_version
Type: string
Required: false
Default: 4.13
MicroShift version to install, in semver format. Major.Minor will determine which repos are enabled.


Dependencies
------------

None

Example Playbook
----------------

    ---
    - name: Run Microshift rpm install role
      hosts: all
      gather_facts: true
      tasks:
        - name: Install Microshift on rpm based system
          ansible.builtin.import_role:
            name: edge.microshift.rpm_install

License
-------

GPLv3
