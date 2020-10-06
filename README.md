# odoo_instalacao 12


```sh
sudo passwd root
```


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


# Gdata
cd /opt/odoo

sudo wget https://pypi.python.org/packages/a8/70/bd554151443fe9e89d9a934a7891aaffc63b9cb5c7d608972919a002c03c/gdata-2.0.18.tar.gz

sudo tar zxvf gdata-2.0.18.tar.gz

sudo chown -R odoo: gdata-2.0.18

sudo -s

cd gdata-2.0.18/

python setup.py install

exit



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

sudo apt-get install python3-software-properties

sudo vim /etc/apt/sources.list.d/pgdg.list

Add a line for the repository: 

deb http://apt.postgresql.org/pub/repos/apt/ xenial-pgdg main

wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

sudo apt-get update

sudo apt-get install postgresql-9.6



# Criar Databse usuario

sudo su postgres

cd

createuser -s odoo

createuser -s roberto

exit



# Iniciar Odoo

cd /opt/odoo/odoo

./odoo-bin --config=odoo.conf



# TROUBLESHOOTING

Any error related to libfontconfig, libxrender not found then:

sudo apt-get -f install libxrender1 libjpeg-turbo8 libfontconfig1 fonts-dejavu-core ttf-bitstream-vera fonts-freefont-ttf gsfonts libfontenc1 libxfont1 x11-common xfonts-encodings xfonts-utils gsfonts-x11 fontconfig-config libfontconfig1 fontconfig


Fonte: http://www.comdesk.com.br/blog/10-instalacao-odoo-v12-no-ubuntu-18-04
Fonte: https://www.systemsvalley.com/odoo-12-installation-on-ubuntu-18-04/
