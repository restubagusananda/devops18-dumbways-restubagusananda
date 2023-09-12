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

**1. Buat direktorik /etc/nginx/dumbways menggunakan super user**
```bash
sudo mkdir /etc/nginx/dumbways
``` 

**2. Tambahkan direktori yang sudah kita buat tadi ke nginx.conf**
```bash
sudo nano /etc/nginx/nginx.conf
``` 
![image](https://github.com/restubagusananda/scrn-day6-w2/blob/89b0fa789f52969f3d9ccc1740726a045f38dd8c/Cuplikan%20layar%202023-09-13%20004135.png)

Kemudian tambahkan
```bash
include /etc/nginx/dumbways/*;
```

![image](https://github.com/restubagusananda/scrn-day6-w2/blob/89b0fa789f52969f3d9ccc1740726a045f38dd8c/Cuplikan%20layar%202023-09-13%20004106.png)

**3. Buat file .conf pada /etc/nginx/dumbways dan isikan script berikut**
```bash
sudo nano reverse-proxy
``` 

```bash
server {
    server_name mawar.mv;

    location / {
        proxy_pass http://127.0.0.1:3000;
    }
}
``` 


**4. setting host pada windows**

buka file explorer lalu menuju direktori C:\Windows\System32\drivers\etc


**5. buka file host dengan notepad yang dijalankan sebgai admin lalu tambahkan ip server anda dengan domain**

![image](https://github.com/restubagusananda/scrn-day6-w2/blob/0af5438362b44bba5bd66b14e66e8f30b5aa3f1b/Cuplikan%20layar%202023-09-13%20012219.png)


**6. cek konfigurasi dengan menjalankan perintah**

```
sudo nginx -t
```

**7. Jika sudah sekarang kita tinggal melakukan reload dan mengecek status Nginx**

```
sudo systemctl reload nginx
```

```
sudo systemctl status nginx
```


**8. Jalankan perintah npm start di direktori dumbflix-frontend dan cek domain tadi**


**9. buka browser dan akses domain yang sudah dibuat tadi**

![image](https://github.com/restubagusananda/scrn-day6-w2/blob/0af5438362b44bba5bd66b14e66e8f30b5aa3f1b/Cuplikan%20layar%202023-09-13%20012333.png)
