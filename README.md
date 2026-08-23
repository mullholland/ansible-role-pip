# [Ansible role pip](#pip)

Installs python pip (and setuptools). Note: this role no longer installs packages via pip itself — see [Role Variables](#role-variables) below.

|GitHub|Downloads|Version|
|------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-pip/actions/workflows/molecule.yml/badge.svg)](https://github.com/mullholland/ansible-role-pip/actions/workflows/molecule.yml)|[![downloads](https://img.shields.io/ansible/role/d/mullholland/pip)](https://galaxy.ansible.com/mullholland/pip)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-pip.svg)](https://github.com/mullholland/ansible-role-pip/releases/)|
## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/mullholland/ansible-role-pip/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  roles:
    - role: "mullholland.pip"
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/mullholland/ansible-role-pip/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: true
  gather_facts: true

  tasks:
    - name: Update apt cache
      ansible.builtin.apt:
        update_cache: true
      when:
        - ansible_facts['os_family'] == "Debian"
```

## [Role Variables](#role-variables)

This role has no configurable variables. It only installs `python3-pip` (and `python3-setuptools`) via the OS package manager.

Installing packages via `pip` was removed in v2.0.0, since pip refuses global installs on systems with [PEP 668](https://peps.python.org/pep-0668/) externally-managed environments (e.g. Debian Bookworm). Install packages you need with `ansible.builtin.pip` directly in your own role/playbook instead.

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/mullholland/ansible-role-pip/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[mullholland.repository_epel](https://galaxy.ansible.com/mullholland/repository_epel)|[![Build Status GitHub](https://github.com/mullholland/ansible-role-repository_epel/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-repository_epel/actions)|[![Build Status GitLab](https://gitlab.com/opensourceunicorn/ansible-role-repository_epel/badges/master/pipeline.svg)](https://gitlab.com/opensourceunicorn/ansible-role-repository_epel)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://mullholland.net) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/mullholland/ansible-role-pip/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/r/mullholland/enterpriselinux)|all|
|[Amazon](https://hub.docker.com/r/mullholland/amazonlinux)|Candidate|
|[Fedora](https://hub.docker.com/r/mullholland/fedora/)|all|
|[Ubuntu](https://hub.docker.com/r/mullholland/ubuntu)|all|
|[Debian](https://hub.docker.com/r/mullholland/debian)|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-pip/issues).

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-pip/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)
