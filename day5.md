# Manage server in terminal
## Text Manipulation
Pada dasarnya kita bisa melakukan manipulasi pada sebuah file menggunakan terminal, tanpa menggunakan teks editor seperti nano.

**1. cat**

Untuk membuat suatu file baru dengan langsung memasuk-kan teks tanpa perlu menggunakan text editor dapat menjalankan perintah:

```shell
cat > (file-name)
```

![image](https://github.com/restubagusananda/scrn-week2-d2/blob/f0e882abdc02599bfa5311b059fd7c07623f12c4/Cuplikan%20layar%202023-09-12%20230546.png)

**2. sed**

Sed adalah singkatan dari stream editor. Gunanya untuk memanipulasi teks dasar pada file. Dengan sed kita dapat mengganti teks dengan cepat.

Contoh penggunaan :

```
sed -i 's/mawar/ros/g' (file-name)
```

![image](https://github.com/restubagusananda/scrn-week2-d2/blob/f0e882abdc02599bfa5311b059fd7c07623f12c4/Cuplikan%20layar%202023-09-12%20230648.png)

**3. grep**

Grep merupakan perintah untuk melakukan pencarian sebuah text dalam sebuah file yang telah dibuat.
Contoh penggunaan :

```
grep ros (file-name)
```

![image](https://github.com/restubagusananda/scrn-week2-d2/blob/0b14672714548fd9dd57ee989cb476e1329022e8/Cuplikan%20layar%202023-09-12%20231409.png)

**4. sort**

Sort untuk mengurutkan data, baik itu secara ascending atau descending.

Berikut adalah contoh penggunaan :

```
sort (file-name)
```

![image](https://github.com/restubagusananda/scrn-week2-d2/blob/bc13d7e02b3bac92c3dab937af3782ae9fc1cc3b/Cuplikan%20layar%202023-09-12%20232020.png)


**5. echo**
Echo digunakan untuk mencetak string / pesan dari hasil perintah lain.

Berikut adalah contoh penggunaan

```
echo "(text)" >/>> (file-name)
```
![image](https://github.com/restubagusananda/scrn-week2-d2/blob/35da32618c26c230fc0f3a2e25abd0a32285bf69/Cuplikan%20layar%202023-09-12%20232859.png)

## Tool htop dan nmon

**1.htop**

htop merupakan perintah untuk memonitoring sistem, kita dapat melihat penggunaan memory, cpu, swap.

Berikut adalah contoh penggunaan :

```
htop
```
Jika pada server kalian belum terinstall, maka dapat menjalankan perintah beriku:
```
sudo apt install htop -y
```
```
htop
```

![image](https://github.com/restubagusananda/scrn-week2-d2/blob/a8f3405c1d17a4adc183abd3facbf6f0e2670cf2/Cuplikan%20layar%202023-09-12%20233606.png)

Keterangan :

- CPU adalah berapa jumlah core yang kita miliki.
- Mem adalah total penggunaan memory.
- Swp adalah Memory cadangan.
- Tasks adalah aplikasi yang sedang berjalan di server.
- Load average adalah rata-rata aplikasi yang berjalan.
- Uptime adalah berapa lama server kita hidup.
- PID adalah nomor proses id setiap proses yang berjalan di linux.
- VIRT adalah memory yang terpakai.
- Command adalah perintah apa yang sedang di jalankan.

**2. nmon**

Pada tampilan awal terdapat beberapa pilihan yang dapat kita gunakan, berikut hanyalah contoh penggunaannya :

Untuk instalasi nmon dapat menggunakan perintah berikut :

```
sudo apt install nmon
```

Untuk menjalankan nmon kalian dapat menggunakan perintah dibawah ini

```
nmon
```

![image](https://github.com/restubagusananda/scrn-week2-d2/blob/a8f3405c1d17a4adc183abd3facbf6f0e2670cf2/Cuplikan%20layar%202023-09-12%20233711.png)




## BASH script untuk instalasi nGinx

Anda dapat membuat skrip BASH sederhana untuk menginstal Nginx dengan perintah berikut.
Pertama buatlah file dengan nama <b>install_nginx.sh</b> dengan menjalankan perintah:

```shell
nano install_nginx.sh
```
Lalu masukan perintah berikut pada text editor:

```shell
#!/usr/bin/env bash

sudo apt update
sudo apt install nginx -y
sudo ufw allow 'Nginx Full'
sudo ufw status
sudo systemctl status nginx
```

Terdapat 6 perintah yang dimasukan pada Script diatas secara berurutan yaitu, Update Repository, Install Nginx, UFW Open Port Nginx Full, Cek Status UFW, Cek Status Nginx 

### Jalankan Script
<img width="1440" src="https://github.com/restubagusananda/scrn-week2-d2/blob/179d147277eb6f36c6c8e676f5029542ab8caa2c/Cuplikan%20layar%202023-09-12%20235453.png">
Setelah itu jalankan BASH Script dengan menjalankan perintah:

```shell
sh install_nginx.sh
```
![image](https://github.com/restubagusananda/scrn-week2-d2/blob/179d147277eb6f36c6c8e676f5029542ab8caa2c/Cuplikan%20layar%202023-09-12%20235616.png)
