## Как протестировать поддомены на localhost (NGINX + Linux)

### 1. Открываем /etc/hosts и указываем, что localhost может иметь поддомены
```
sudo nano /etc/hosts
```

Меняем строку 
```
127.0.0.1 localhost
```
на
```
127.0.0.1 *.localhost
```

### 2. Опишем сервер в файле /sites-available/default
```
sudo nano /etc/nginx/sites-available/default
```

```
server {
  listen 80 default_server;
  root /var/www/html/errors/404;
  server_name *.localhost *.<host-name>;

  location / {
    index subdomain.html;
  }

}
```

### 3. Перезапускаем NGINX
```
sudo service nginx reload
```
