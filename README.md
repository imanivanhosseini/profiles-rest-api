# Profiles REST API

Profiles REST API course code.

## Notes:

- Create a developement server using vagrant
  - `profiles-rest-api git:(master) vagrant init ubuntu/bionic64`
- Start a vagrant box on our machine:
  - `profiles-rest-api git:(master) vagrant up`
- Connect to vagrant server:
  - `profiles-rest-api git:(master) vagrant ssh`
- - Disconnect from vagrant server:
  - `profiles-rest-api git:(master) exit`

---

- Create a python virtual environment:
  - `vagrant@ubuntu-bionic:~$ cd /vagrant/`
  - `vagrant@ubuntu-bionic:/vagrant$ python -m venv ~/env`
    - This command creates a new file in our vagrant server, home directory called env
    - ~ will create the environment in the home directory of the vagrant server as opposed to the vagrant folder which is synchronized to our local machine.
  - Activate the virtual environment:
    - `vagrant@ubuntu-bionic:/vagrant$ source ~/env/bin/activate`
  - Deactivate the virtual environemt:
    - `(env) vagrant@ubuntu-bionic:/vagrant$ deactivate`
  - Download the python packages:
    - First, make sure that you are in vagrant directory and the python environment is activated
      - `vagrant@ubuntu-bionic:$ cd /vagrant/`
      - `vagrant@ubuntu-bionic:/vagrant$`
        /vagrant
      - `vagrant@ubuntu-bionic:/vagrant$ source ~/env/bin/activate`
    - Second, run the following command:
      - `(env) vagrant@ubuntu-bionic:/vagrant$ pip install -r requirements.txt`

---

- Create a new Django project and app:
  - `(env) vagrant@ubuntu-bionic:/vagrant$ django-admin startproject profiles_project .`
    - It creates the project named _profiles_project_ and _._ is the location where we want our projects gets created. Dot(.) is optional. If we don't specify it then it will create a new sub folder so profiles_project which is not what we want.
- Create an app within our project:
  - `(env) vagrant@ubuntu-bionic:/vagrant$ python manage.py startapp profiles_api`

---

- Enable our app in django setting:
  - 1.  Open "profiles_project" and open up \_settings.py\*
  - 2.  Add _rest_framework_, _rest_framework.authtoken_ and _profiles_api_, to the **INSTALLED_APPS** list.
- Start a django development web server:
  - `(env) vagrant@ubuntu-bionic:/vagrant$ python manage.py runserver 0.0.0.0:8000`
  - In our Vagrantfile we mapped port 8000 on our host machine and that's why we specify port 8000 when we start the server
    - Check this code in the Vagrantfile: `config.vm.network "forwarded_port", guest: 8000, host: 8000`
    - Open a browser and go to http://127.0.0.1:8000/

---

- Create migration and sync database:
  - `(env) vagrant@ubuntu-bionic:/vagrant$ python manage.py makemigrations profiles_api`
  - `(env) vagrant@ubuntu-bionic:/vagrant$ python manage.py migrate`
