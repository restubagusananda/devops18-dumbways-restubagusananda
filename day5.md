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

Anda dapat membuat skrip BASH sederhana untuk menginstal Nginx dengan perintah berikut:

```bash
#!/bin/bash

# Periksa apakah script dijalankan sebagai superuser
if [ "$EUID" -ne 0 ]; then
    echo "Skrip ini harus dijalankan sebagai superuser (root)." >&2
    exit 1
fi

# Perbarui cache paket
apt update

# Instal Nginx
apt install -y nginx

# Mulai Nginx
systemctl start nginx

# Aktifkan Nginx untuk dijalankan saat boot
systemctl enable nginx

# Tampilkan pesan sukses
echo "Nginx telah berhasil diinstal dan diaktifkan."

exit 0
```

Simpan skrip ini dalam file dengan ekstensi `.sh`, misalnya `install_nginx.sh`, dan berikan izin eksekusi dengan perintah:

```bash
chmod +x install_nginx.sh
```

Kemudian, jalankan skrip tersebut dengan perintah berikut:

```bash
sudo ./install_nginx.sh
```

Skrip ini akan memeriksa apakah Anda menjalankannya sebagai superuser, kemudian memperbarui cache paket, menginstal Nginx, dan mengaktifkannya untuk dijalankan secara otomatis saat sistem boot. Setelah selesai, Anda akan melihat pesan bahwa Nginx telah berhasil diinstal dan diaktifkan.

![image](https://github.com/irwanpanai/devops18-dumbways-irwanpanai/assets/89429810/0d1fa2f1-c714-4686-b651-4edb77f34129)

keterangan : kondisi jika skrip dijalankan tidak sebagai superuser(root)

![image](https://github.com/irwanpanai/devops18-dumbways-irwanpanai/assets/89429810/e5a8c5f7-2744-4c52-acc9-8cf963ae5836)

keterangan : kondisi jika menjalankan skrip dengan superuser(root)

cek localhost
![image](https://github.com/irwanpanai/devops18-dumbways-irwanpanai/assets/89429810/3518dcb1-39d4-4911-9e21-47ebe54815d4)

