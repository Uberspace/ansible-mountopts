# Ansible Mount Options

An Ansible module which allows to easily add, remove or set mount options in
`/etc/fstab`. The original [`mount`-module](http://docs.ansible.com/ansible/mount_module.html)
in ansible only allows setting the whole mount option list. This can be
troublesome when editing mount options of a partly-automated remote or when
editing options from multiple roles.

Note that the scope of module _only_ only includes mount options. It does not
support changing the file system type of a mount, nor does it support adding,
removing or mounting mount points. Use the original ansible module for that.

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
