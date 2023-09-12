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
grep dumbways file3
```

![image]()

**4. sort**

Sort untuk mengurutkan data, baik itu secara ascending atau descending.

Berikut adalah contoh penggunaan :

```
sort file4
```

![image]()
