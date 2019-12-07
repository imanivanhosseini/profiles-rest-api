# Profiles REST API

Profiles REST API course code.

## Notes:

- Connect to vagrant server:
  - `vagrant ssh`
- Create a python virtual environment:
  - `vagrant@ubuntu-bionic:/vagrant\$ python -m venv ~/env`
    - This command creates a new file in our vagrant server, home directory called env
    - ~ will create the environment in the home directory of the vagrant server as opposed to the
      vagrant folder which is synchronized to our local machine.
  - Activate the virtual environment:
    - `vagrant@ubuntu-bionic:/vagrant\$ source ~/env/bin/activate`
  - Deactivate the virtual environemt:
    - `(env) vagrant@ubuntu-bionic:/vagrant\$ deactivate`
