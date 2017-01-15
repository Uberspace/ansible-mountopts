# Ansible MountOpts

An Ansible module which allows to easily add, remove or set
mount options in `/etc/fstab`.

## Usage

```yml
# set the data-option to 'journal'
- mountopts:
    name: /
    option: data
    value: journal

# remove the 'noatime' from /home entirely
- mountopts:
    name: /home
    option: noatime
    state: absent
```

For more examples take a look at `test/test.yml`, which contains all possible
use cases.

## Installation

It is recommended to add this repository as a [git submodule](https://git-scm.com/docs/git-submodule)
to your ansible project. The `library/mountopts.py`-file can then be symlinked
into your `library` directory. Alternatively the [`library`-setting](http://docs.ansible.com/ansible/intro_configuration.html#library)
of ansible can be used to point ansible to the submodule directly.

### Dependencies

This module depends on the [`fstab`-python-module](https://pypi.python.org/pypi/fstab),
which needs to be installed separately on the remote machine:

```yml
- name: install dependencies for mountopts-module
  pip: name=fstab
```

## Development

1. first get an virtualenv up and running: `virtualenv venv --python=python2`
2. activate the venv: `source venv/bin/activate`
3. install dependencies: `pip install -r requirements.txt`
4. run the test-playbook in `test`: `ansible-playbook test.yml`
5. ???
6. profit!
