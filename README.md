### Yii2VN - CMS base on Yii Framework version 2

[![Join the chat at https://gitter.im/sieulog/yii2cms](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/sieulog/yii2cms?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

#### Server information
* Nginx
* HHVM
* Redis
* MySQL

#### Example config virtual host in Nginx Server

```bash

server {
	set $ROOT /home/sieulog/Web;
	listen 80;
	root $ROOT;
	index index.html index.htm index.php;
	server_name localhost;
	include hhvm.conf;
	location / {
		root $ROOT/frontend/web;
		try_files $uri /frontend/web/index.php?$args;
	}

	location ~* \.(htaccess|htpasswd|svn|git) {
		deny all;
	}

	location /admin {
		alias $ROOT/backend/web;
		try_files $uri /backend/web/index.php?$args;
	}
}

```

#### Example config virtual host in Apache Server

```bash

<VirtualHost *:80>
	ServerName localhost
	DocumentRoot "/home/sieulog/Web"
	<Directory "/home/sieulog/Web">
		AllowOverride all
        Order allow,deny
        Allow from all
		Require all granted
	</Directory>
</VirtualHost>

```

#### Initial Yii2

```bash

$ php init

```
