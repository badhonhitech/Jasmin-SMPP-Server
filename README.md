# Jasmin SMPP Panel (Server)
Jasmin SMPP Panel With MySQL Enable for Jasmin SMS Gateway. Need to setup contact with **skype: helios-sw**

# Technology Stack
- Ubuntu 18.04.3 LTS
- Django
- LAMP (Linux, Apache, MySQL, PHP) 

## Installation
Complete Things To Do After Install Ubuntu. Download and Extract folder. I recommend installing in a virtualenv!

Install dependencies:

```shell
$ pip install -r requirements.pip
```
cd to **JasminSMPPPanel** and run:
```shell
$ ./manage.py migrate 
$ ./manage.py createsuperuser 
$ ./manage.py collectstatic
```
The last is only needed if you are running the production server (see below) rather than the Django dev server. It should be run again on any upgrade that changes static files. If in doubt, run it.

You can also override the default settings for the telnet connection in local_settings.py. These settings with their defaults are:
```python
TELNET_HOST = '127.0.0.1'
TELNET_PORT = 8990
TELNET_USERNAME = 'jcliadmin'
TELNET_PW = 'jclipwd'
```
## Running

To run for testing and development: 
```shell
./manage.py runserver
sudo python manage.py runserver [::]:8000
```
This is slower, requires `DEBUG=True`, and is much less secure

## Deployment
To run on production:
```shell
$ sudo apt-get install apache2 libapache2-mod-wsgi
$ cp 000-default.conf /etc/apache2/sites-available/000-default.conf
$ sudo a2enmod wsgi
$ a2ensite 000-default.conf
$ service apache2 restart

```shell
./run_cherrypy.py
```
This requires that you run the collectstatic command (see above) and you should have `DEBUG=False`.

## Contributes
Inspired by [Jasmin API](https://github.com/jookies/jasmin-api)
