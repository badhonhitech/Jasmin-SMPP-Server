# Jasmin SMPP Panel (Server)
Jasmin SMPP Panel for Jasmin SMS Gateway. Need to setup contact with **skype: helios-sw**

# Technology Stack
- Ubuntu 18.04.3 LTS
- Django
- Apache
- SQlite
- Git

## Installation

***1st Phase***
Complete Things To Do After Install Ubuntu:

```shell
sudo apt update && sudo apt-get upgrade --fix-missing 
sudo apt install build-essential checkinstall
sudo apt install ubuntu-restricted-extras
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt update
sudo apt install launchpad-getkeys
sudo launchpad-getkeys 
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git
sudo git config --global user.name "YourName"
sudo git config --global user.email youremail@gmail.com
sudo apt list --upgradable
sudo apt upgrade -y
sudo apt -y autoclean 
sudo apt -y clean 
sudo apt update
sudo reboot
```

***2nd Phase***
Install Apache+clone repository to /var/www/:
```shell

sudo apt update
sudo apt-get install apache2 libapache2-mod-wsgi
sudo ufw allow 'Apache'
sudo systemctl enable apache2
sudo systemctl restart apache2
sudo systemctl reload apache2
cd /var/www/
git clone https://github.com/itelservices/JasminSMPPPanel.git
sudo rm -rf html
sudo mv JasminSMPPPanel html
cd html
sudo apt install python-pip
sudo pip install -r requirements.pip
sudo ./manage.py migrate 
sudo ./manage.py createsuperuser 
sudo ./manage.py collectstatic
```
If you are running the production server (see below) rather than the Django dev server. It should be run again on any upgrade that changes static files. If in doubt, run it.

You can also override the default settings for the telnet connection in local_settings.py. These settings with their defaults are:

```python
TELNET_HOST = '127.0.0.1'
TELNET_PORT = 8990
TELNET_USERNAME = 'root'
TELNET_PW = 'password'
```
## Running

To run for testing and development: 
```shell
sudo python manage.py runserver [::]:8000
```

## Deployment
To run on production:
```shell
cp 000-default.conf /etc/apache2/sites-available/000-default.conf
sudo a2enmod wsgi
sudo a2ensite 000-default.conf
sudo service apache2 restart
sudo chmod a+w db.sqlite3
cd ..
sudo chown root:root html
sudo service apache2 restart
sudo chown www-data:www-data html
cd html
sudo chown www-data:www-data db.sqlite3 
sudo service apache2 reload
```

## visit
http://72.255.34.254:8001

## Rebuild By: Skype: helios-sw
