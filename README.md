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
wget -qO - http://bit.ly/jasmin-deb-repo | sudo bash
sudo apt-get install python-jasmin
sudo systemctl enable jasmind
sudo systemctl start jasmind

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
sudo git clone https://github.com/amechax/JasminWebPanel.git
sudo rm -rf html
sudo mv JasminWebPanel html
cd html
sudo apt install python-pip
sudo pip install -r requirements.pip
sudo ./manage.py migrate 
sudo ./manage.py createsuperuser 
sudo ./manage.py collectstatic
```
## Running
http://localhost/

