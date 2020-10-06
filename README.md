# odoo_instalacao 12


sudo passwd root


# Preparação do Linux
sudo apt update && sudo apt upgrade

sudo apt install git gcc python3-pip build-essential python3-dev python3-venv python3-wheel libxslt-dev libzip-dev libpq-dev libldap2-dev libsasl2-dev python3-setuptools python3-pypdf2

pip3 install Babel decorator docutils ebaysdk feedparser gevent greenlet html2text Jinja2 lxml Mako MarkupSafe mock num2words ofxparse passlib Pillow psutil psycogreen psycopg2 pydot pyparsing PyPDF2 pyserial python-dateutil python-openid pytz pyusb PyYAML qrcode reportlab requests six suds-jurko vatnumber vobject Werkzeug XlsxWriter xlwt xlrd

pip3 install pyldap beautifulsoup4 python-stdnum

sudo apt-get install python3-suds

sudo apt-get install python-gevent -y

sudo apt-get install -y npm

sudo ln -s /usr/bin/nodejs /usr/bin/node

sudo npm install -g less less-plugin-clean-css rtlcss

sudo apt-get install node-less

sudo python3 -m pip install libsass

sudo apt-get install software-properties-common

# Wkhtmltopdf
cd /tmp
wget https://builds.wkhtmltopdf.org/0.12.1.3/wkhtmltox_0.12.1.3-1~bionic_amd64.deb
sudo apt install ./wkhtmltox_0.12.1.3-1~bionic_amd64.deb
sudo ln -s /usr/local/bin/wkhtmltopdf /usr/bin
sudo ln -s /usr/local/bin/wkhtmltoimage /usr/bin

# Odoo

cd /opt/odoo
sudo git clone --depth 1 --branch 12.0 https://www.github.com/odoo/odoo /opt/odoo/odoo-server/
cd /opt/odoo/odoo-server
sudo pip3 install -r requirements.txt

sudo mkdir /var/log/odoo
cd /var/log/odoo
sudo touch odoo-server.log
sudo chown -R odoo:root /var/log/odoo
sudo chown -R odoo:odoo /opt/odoo/*
sudo nano /etc/odoo-server.conf

# conteudo arquivo .conf
[options]
;This is the password that allows database operations:
admin_passwd = odoo123456
db_host = False
db_port = False
db_user = odoo
db_password = False
xmlrpc_port = 8069
logfile = /var/log/odoo/odoo-server.log
addons_path = /opt/odoo/odoo-server/addons
# fim conteudo arquivo .conf

sudo chown odoo: /etc/odoo-server.conf
sudo chmod 640 /etc/odoo-server.conf

# POSTGRES


Fonte: http://www.comdesk.com.br/blog/10-instalacao-odoo-v12-no-ubuntu-18-04
