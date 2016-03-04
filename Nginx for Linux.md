#AWS

## set server time zone date

> dpkg-reconfigure tzdata		
> asia		
> taipei

## add user

> adduser leo_wang		

## install webserver of nginx

> apt-get install nginx

## Install php fpm, php mysql, php-cli, php5-mcrypt, php5-curl, php5-imagick, php-gd

> apt-get install php5-fpm php5-mysql php5-cli php5-mcrypt php5-curl php5-imagick php5-gd			
> apt-get install php5-memcached memcached		
> php5enmod mcrypt

## Add or Modifiy /etc/nginx/nginx.conf

> client_max_body_size 128M;    
> worker_processes 2; (if instance core is 2 機器核心數量)

## Add or Modifiy /etc/php5/fpm/php.ini 
> cgi.fix_pathinfo = 0
> mbstring.internal_encoding = UTF-8 (unucomment)
> max_input_vars = 5000

## Modify /etc/php5/fpm/pool.d/www.conf

for web: 
> pm.max_children = 50		
> pm.start_servers = 10		
> pm.min_spare_servers = 5		
> pm.max_spare_servers = 15

for fps: 
> pm.max_children = 100		
> pm.start_servers = 40		
> pm.min_spare_servers = 20		
> pm.max_spare_servers = 60

## Add a EBS to this instance which position at /storage/mysql (only on Dev)

> mount /dev/svdf /storage/mysql

## Install MySQL and set /etc/mysql/my.cnf (only on Dev)

> apt-get install mariadb-server		
> set datadir = /storage/mysql/data		
> set default-time-zone = ‘+8:00’

## Install graph handler imagemagic libaray

> apt-get install imagemagick

* convert for anyone and it’s orginal path is /etc/alternatives/convert (黑名單機制，選配)

## SSH use password login

> sudo vi /etc/ssh/sshd_config

### modifity 
PasswordAuthentication yes
PubkeyAuthentication no
