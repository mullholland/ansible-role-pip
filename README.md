# [pip](#pip)

install and configure virtual environments with pip

|GitHub|GitLab|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-pip/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-pip/actions)|[![gitlab](https://gitlab.com/opensourceunicorn/ansible-role-pip/badges/master/pipeline.svg)](https://gitlab.com/opensourceunicorn/ansible-role-pip)|[![quality](https://img.shields.io/ansible/quality/)](https://galaxy.ansible.com/mullholland/pip)|[![downloads](https://img.shields.io/ansible/role/d/)](https://galaxy.ansible.com/mullholland/pip)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-pip.svg)](https://github.com/mullholland/ansible-role-pip/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/mullholland/ansible-role-pip/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  vars:
    pip_packages:
      - "python-dateutil"

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

  roles:
    - role: mullholland.repository_epel

  tasks:
    - name: Update apt cache
      ansible.builtin.apt:
        update_cache: true
      when:
        - ansible_os_family == "Debian"
```


## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/mullholland/ansible-role-pip/blob/master/defaults/main.yml):

```yaml
---
# By default no modules should be installed. Note: This does not work on Debian Bookworm.
# See https://peps.python.org/pep-0668/

# WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour
# with the system package manager. It is recommended to use a virtual environment
# instead: https://pip.pypa.io/warnings/venv
# For example the variables `python_pip_venvs` down below
# Define pip packages
pip_packages: []
#  - "python-dateutil"
#  - "python-dateutil==0.11"
#  - "python-dateutil>=1.1,<=2.1"
#  - "python-dateutil>=1"
pip_packages_group: []
pip_packages_host: []

# Update pip using pip before installing packages
pip_update: true

# You can use something other than the default pip binary.
# python_pip_executable: pip3
```

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
|[EL](https://hub.docker.com/repository/docker/mullholland/docker-centos-systemd/general)|all|
|[Amazon](https://hub.docker.com/repository/docker/mullholland/docker-amazonlinux-systemd/general)|Candidate|
|[Fedora](https://hub.docker.com/repository/docker/mullholland/docker-fedora-systemd/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/mullholland/docker-ubuntu-systemd/general)|all|
|[Debian](https://hub.docker.com/repository/docker/mullholland/docker-debian-systemd/general)|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-pip/issues)

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-pip/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)

Please consider [sponsoring me](https://github.com/sponsors/mullholland).
