#This Tutorial
```
apt-get install ca-certificates
apt-get update && apt-get -y install mysql-server
```
```
input name & password database
```
```
mysql_secure_installation
```
```
input pass (n,y,y,y,y,y)
```
```
chown -R mysql:mysql /var/lib/mysql/ && chmod -R 755 /var/lib/mysql/
```
```
apt-get -y install nginx php5 php5-fpm php5-cli php5-mysql php5-mcrypt
```
```
rm /etc/nginx/sites-enabled/default && rm /etc/nginx/sites-available/default
mv /etc/nginx/nginx.conf /etc/nginx/nginx.conf.backup
mv /etc/nginx/conf.d/vps.conf /etc/nginx/conf.d/vps.conf.backup
wget -O /etc/nginx/nginx.conf "http://script.hostingtermurah.net/repo/blog/ocspanel-debian7/nginx.conf"
wget -O /etc/nginx/conf.d/vps.conf "http://script.hostingtermurah.net/repo/blog/ocspanel-debian7/vps.conf"
sed -i 's/cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/g' /etc/php5/fpm/php.ini
sed -i 's/listen = \/var\/run\/php5-fpm.sock/listen = 127.0.0.1:9000/g' /etc/php5/fpm/pool.d/www.conf
```
```
useradd -m vps && mkdir -p /home/vps/public_html
rm /home/vps/public_html/index.html && echo "<?php phpinfo() ?>" > /home/vps/public_html/info.php
chown -R www-data:www-data /home/vps/public_html && chmod -R g+rw /home/vps/public_html
service php5-fpm restart && service nginx restart
```
```
mysql -u root -p
```
```
CREATE DATABASE IF NOT EXISTS OCSPANEL;EXIT;
```
```
apt-get -y install git
```
```
cd /home/vps/public_html
git init
git remote add origin https://github.com/MiraApsari/gaje.git
git pull origin master
chmod 777 /home/vps/public_html/config
chmod 777 /home/vps/public_html/config/config.ini
chmod 777 /home/vps/public_html/config/route.ini
```
```
rm -R /home/vps/public_html/installation
```
```
