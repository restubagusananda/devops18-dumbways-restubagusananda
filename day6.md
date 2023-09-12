# Day 7 - Web Server & Reverse Proxy

## 1. Running Dumbflix using PM2

1. Gunakan node 10
```bash
nvm use 10
``` 
<img src="images/image001.png">

2. Masuk ke direktori dumbflix dan running menggunakan PM2
```bash
cd dumbflix-frontend/
pm2 start npm --name "dumb-flix" -- start
``` 
<img src="images/image002.png">

## 2. Create Reverse Proxy

1. Buat direktorik /etc/nginx/dumbways menggunakan super user
```bash
sudo mkdir /etc/nginx/dumbways
``` 
<img src="images/image003.png">

2. Tambahkan direktori yang sudah kita buat tadi ke nginx.conf
```bash
sudo nano /etc/nginx/nginx.conf
``` 

Kemudian tambahkan
```bash
include /etc/nginx/dumbways/*;
``` 
<img src="images/image004.png">

3. Buat file .conf pada /etc/nginx/dumbways dan isikan script berikut
```bash
sudo nano /etc/nginx/dumbways/flix.conf
``` 

```bash
server {
    server_name flix.com;

    location / {
        proxy_pass http://192.168.0.11:3000;
    }
}
``` 
<img src="images/image005.png">

4. Reload nginx dan mencoba di browser flix.com
```bash
sudo systemctl reload nginx
``` 
<img src="images/image006.png">

[**Back**](../../README.md)
