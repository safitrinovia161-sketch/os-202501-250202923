
# Laporan Praktikum Minggu [X]
Topik: Linux fs Permission

---

## Identitas
- **Nama**  : Novia Safitri  
- **NIM**   : 25020923  
- **Kelas** : 1IKRA

---

## Tujuan
1.Menggunakan perintah ls, pwd, cd, cat untuk navigasi file dan direktori.

2.Menggunakan chmod dan chown untuk manajemen hak akses file.

3.Menjelaskan hasil output dari perintah Linux dasar.

4.Menyusun laporan praktikum dengan struktur yang benar.

5.Mengunggah dokumentasi hasil ke Git Repository tepat waktu.


---

## Dasar Teori
File dan direktori di Linux tersusu seperti pohon dengan satu titik awal yang disebut root (/).Setiap file memiliki pemilik dan grup yang mengatur hak akses membaca,menulis ,dan menjalankan file.Hak akses file ini penting untuk keamanan dan dapat diubah dengan perintah khusus agar hanya pengguna yang berhak mengakses file.

---

## Langkah Praktikum
1.Setup Environment

Gunakan Linux (Ubuntu/WSL).
Pastikan folder kerja berada di dalam direktori repositori Git praktikum:

     praktikum/week3-linux-fs-permission/

2.Eksperimen 1 – Navigasi Sistem File Jalankan perintah berikut:

     pwd
    ls -l
    cd /tmp
    ls -a
Jelaskan hasil tiap perintah.

Catat direktori aktif, isi folder, dan file tersembunyi (jika ada).

3.Eksperimen 2 – Membaca File Jalankan perintah:

    cat /etc/passwd | head -n 5

Jelaskan isi file dan struktur barisnya (user, UID, GID, home, shell).

4.Eksperimen 3 – Permission & Ownership Buat file baru:

     echo "Hello <NAME><NIM>" > percobaan.txt
     ls -l percobaan.txt
    chmod 600 percobaan.txt
    ls -l percobaan.txt

Analisis perbedaan sebelum dan sesudah chmod.
Ubah pemilik file (jika memiliki izin sudo):

     sudo chown root percobaan.txt
     ls -l percobaan.txt
Catat hasilnya.

5.Eksperimen 4 – Dokumentasi
Ambil screenshot hasil terminal dan simpan di:

     
    praktikum/week3-linux-fs-permission/screenshots/
Tambahkan analisis hasil pada laporan.md.

Commit & Push

     git add .
    git commit -m "Minggu 3 - Linux File System & Permission"
    git push origin main


---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
```bash
uname -a
lsmod | head
dmesg | head
```

---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](screenshots/example.png)

---

## Analisis
- Jelaskan makna hasil percobaan.

 
- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).  
- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)?  

---

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.


## Tugas
 1.Dokumentasikan hasil seluruh perintah pada tabel observasi 
| No | Perintah | Fungsi|Hasil/output|Keterangan|
| :--- | :---|:---|:---|:---|
1|pwd|Menampilkan direktori aktif|/home/safitrinovia/|Pengguna sedang berada di direktori homenya sendiri|
2| ls -l|Menampilkan daftar isi direktori beserta detailnya seperti izin akses,user,ukuran,waktu,nama dan file|Total 0|Direktori /home/novia safitri tidak memiliki file apapun |
3|cd /tmp|Pindah ke direktori sementara /tmp|Tidak ada hasil/output|Mengubah posisi kerja aktif menjadi /tmp, tempat file sementara sistem disimpan|
4|ls -a|Menmapilkan semua file di direktori,termasuk file tersembunyi yang awali dengan titik(".")|    .   ..   X11-unix   snap-private-tmp   systemd-private-...|( .) direktori saat ini dan (..)direktori induk serta dotfiles|
5|cat /etc/passwd l head -n 5|Menampilkan 5 baris pertama akun pengguna disistem||cat keluarkan isi /etc/passwd → | (pipe) meneruskan ke head -n 5 untuk hanya melihat 5 baris teratasy yaitu user root memiliki UID 0, GID 0, direktori home /root, dan shell /bin/bash |
6|echo "Hello <NOVIA SAFITRI><25020923>" > percobaan.txt|Membuat file baru  dan menuliskan teks "Hello<NOVIA SAFITRI><25020923>"ke dalamnya |Tidak ada output/ hasil|echo keluarkan string → > redirect menulis ke file (membuat baru atau menimpa file lama)|
7|ls -l percobaan.txt|Menampilkan detail file seperti user,izin,ukuran|    -rw-r--r-- 1 safitrinovia safitrinovia 32 Oct 24 20:34 percobaan.txt| -rw-r--r-- 1 safitrinovia safitrinovia ... → pemilik safitrinovia, izin baca/tulis untuk pemilik, baca untuk grup/lain|
8|chmod 600 percobaan.txt|Mengubah izin akses file menjadi r-x------|tidak ada output|File hanya bisa dibaca dan dijalankan oleh pemilik(NOVIA SAFITRI), tidak bisa diubah oleh pengguna lain|
9|ls -l percobaan.txt|Mengecek perubahan izin |-rw-------1 safitrinovia safitrinovia 32 Oct 24 20:34 percobaan.txt|Terbaca bahwa izin file sudah berubah, grup dan pengguna lain sudah tidak memiliki akses sama sekali|
10|sudo chown root percobaan.txt|Mengubah kepemilikan file menjadi milik pengguna yaitu novia safitri menjadi root|Sekarang file dimiliki oleh root, bukan lagi oleh safitrinovia|chown ubah pemilik/grup dari file; sudo jalankan perintah sebagai admin.Dan sekarang hanya root yang berhak mengakses file seutuhnya|
11|ls -l percobaan.txt|Mengecek perubahan kepemilikan|-rw------- 1 root NOVIA SAFITRI 32 Oct 24 20:34 percobaan.txt|Sekarang pemilik file adalah root sedangkan grup masih milik novia safitri dan file sudah menjadi milik sistem|

2.Jelaskan fungsi tiap perintah dan arti kolom permission (rwxr-xr--).

Jawab : # rwx adalah hak mengakses file pemilik 
        * r artinya boleh baca 
        * w artinya boleh ubah/tulis
        * x artinya boleh dijalankan/ dieksekusi
        #(r-x) adalah hak mengakses file grup
        * r boleh baca
        * - tidak boleh diubah
        * x boleh dijalankan
        # (---)  adalah hak akses untuk lainnya atau publik
        * - tidak ada izin baca,tulis,maupun jalankan 

3.Analisis peran chmod dan chown dalam keamanan sistem Linux.

Peran chmod dan chown dalam keadaan sistem Linux itu sangat penting untuk menjaga keamanan file dan folder .

* chmod yaitu mengatur siapa saja yang boleh membaca,menguubah ,atau menjalankan file.Misalnya hanya pemilik yang boleh mengubah,tapi yang lain hanya boleh melihat atau tidak boleh sama sekali.Chmod mencegah file diubah atau dijalankan sembarangan orang lain. 

* Chown berperan untuk menentukan siapa pemilik file itu,hanya orang tertentu yang punya kontrol penuh dan bisa mengatur izin file tersebut.Jika pemilik dan grup diatur dengan benar,maka akses ke file menjadi lebih terjaga. 
---

## Quiz
1. Apa fungsi dari perintah chmod?

    Jawaban: Chmod berfungsi dalam mengendalikan akses agar proses dan pengelolaan file di sistem Linux dapat berjalan dengan aman dan efisien.
3. Apa arti dari kode permission rwxr-xr--?

    Jawaban: -rwx:pemilik file bisa membaca ,menulis,dan menjalankan file
             -rx:grup hanya bisa baca dan jalankan ,tidak bisa mengubah file
             -r--:pengguna lain hanya bisa membaca,tidak bisa menulis atau               menjakankan.
   Ini cara linux mengtaur siapa yang boleh mengakses dan apa yang boleh mereka lakukan pada file tersebut.
5. Jelaskan perbedaan antara chown dan chmod.
   Jawaban:

Aspek | Chown | Chmod |
  |:--- | :--- | :---|
  Fungsi|Mengganti siapa pemilik dan grup file|Mengatur hak akses yaitu baca,tulis dan eksekusi|
Apa yang diubah|Pemilik(user) file|Izin baca ,tulis ,dan eksekusi|
contoh |Chown user file.txt|Chomod 755 file.txt|
tujuan|Atur siapa pemilik file|Atur siapa yang bisa akses|
siapa yang bisa akses|Pemilik/admin|Pemilik filedan admin|
Perhatian khusus|Harus punya izin atau sebagai root|Digunakan untuk membatasi atau memberi akses|

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?
 Yang paling menantang minguu ini adalah saat saya mendownload ubuntu karena saya selama praktikum belum memakai ubuntu jadi saya baru mendownload,kenapa menantang? ya karena cara downloadnya yang cukup rumit dan lama prosesnya. 
- Bagaimana cara Anda mengatasinya?  
Cara saya mengatasinya dengan menonton tutorial di youtobe jika masih blm bisa saya mencari turotial lainnya 
---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
