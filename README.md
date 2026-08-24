# [Ansible role pip](#pip)

Installs python pip and setuptools via the OS package manager

|GitHub|Downloads|Version|
|------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-pip/actions/workflows/molecule.yml/badge.svg)](https://github.com/mullholland/ansible-role-pip/actions/workflows/molecule.yml)|[![downloads](https://img.shields.io/ansible/role/d/mullholland/pip)](https://galaxy.ansible.com/mullholland/pip)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-pip.svg)](https://github.com/mullholland/ansible-role-pip/releases/)|
## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/mullholland/ansible-role-pip/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  gather_facts: true
  roles:
    - role: "{{ lookup('env', 'MOLECULE_PROJECT_DIRECTORY') }}"
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/mullholland/ansible-role-pip/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  gather_facts: true

  tasks:
    - name: Update apt cache
      ansible.builtin.apt:
        update_cache: true
      when:
        - ansible_facts['os_family'] == "Debian"
```



## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/mullholland/ansible-role-pip/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[mullholland.repository_epel](https://galaxy.ansible.com/mullholland/repository_epel)|[![Build Status GitHub](https://github.com/mullholland/ansible-role-repository_epel/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-repository_epel/actions)|[![Build Status GitLab](https://gitlab.com/mullholland-github-mirror/ansible-role-repository_epel/badges/master/pipeline.svg)](https://gitlab.com/mullholland-github-mirror/ansible-role-repository_epel)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://mullholland.net) for further information.

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

|container|tags|
|---------|----|
|[Fedora](https://hub.docker.com/r/mullholland/fedora/)|all|
|[Ubuntu](https://hub.docker.com/r/mullholland/ubuntu)|all|
|[Debian](https://hub.docker.com/r/mullholland/debian)|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The version before the previous version.
- The previous version.
- The current version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-pip/issues).

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-pip/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)
