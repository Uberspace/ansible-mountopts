# Ansible MountOpts

An Ansible module which allows to easily add, remove or set
mount options in `/etc/fstab`.

## Usage

See `test/test.yml` for usage examples.

## Development

1. first get an virtualenv up and running: `virtualenv venv --python=python2`
2. activate the venv: `source venv/bin/activate`
3. install dependencies: `pip install -r requirements.txt`
4. run the test-playbook in `test`: `ansible-playbook test.yml`
5. ???
6. profit!
