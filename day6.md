# Day 6 - Web Server & Reverse Proxy

## 1. Running Dumbflix using PM2

** Gunakan node 10 **
```bash
nvm use 10
``` 
## Jalankan aplikasi Dumbflix menggunakan PM2

**install PM2 dengan perintah berikut**

```
npm install pm2 -g
```

** masuk ke dirktori src pada dumbflix lalu jalankan PM2**

```
cd dumbflix-frontend/src
```

```
pm2 start index.js
```

![image](https://github.com/restubagusananda/scrn-day6-w2/blob/73e6e8102f5e9779c0d0ca707a54d423690e993f/Cuplikan%20layar%202023-09-13%20002525.png)


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
