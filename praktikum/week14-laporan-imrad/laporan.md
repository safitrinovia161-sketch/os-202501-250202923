
# Laporan Praktikum Minggu [X]
Topik:  Manajemen Proses dan User di Linux
---

## Identitas
- **Nama**  : NOVIA SAFITRI
- **NIM**   : 25020923
- **Kelas** : 1IKRA

---

## Tujuan

1.Menjelaskan konsep proses dan user dalam sistem operasi Linux.
2.Menampilkan daftar proses yang sedang berjalan dan statusnya.
3.Menggunakan perintah untuk membuat dan mengelola user.
4.Menghentikan atau mengontrol proses tertentu menggunakan PID.
5.Menjelaskan kaitan antara manajemen user dan keamanan sistem.

---

## Dasar Teori
Manajemen proses adalah cara mengatur program yang sedang berjalan di komputer.Linux membuat nomor khusus untuk setiap program agar dapat dikenali dan dikendalikan,misalnya memulai,menghentikan,atau memberi prioritas.Manajemen pengguna cara mengatur siapa yang bisa masuk dan menggunakan komputer,setiap orang yang memakai Linux punya akun dengan nama dan pasword sendiri sehingga data/aksesnya aman.Tujuan dari keduanya agar komputer berjalan lancar,semua program dijalankan ddengan baik,dan hanya orang yang mempunya izin yang dapat mengakses sistem.
---

## Langkah Praktikum

1.Setup Environment

Gunakan Linux (Ubuntu/WSL).

Pastikan Anda sudah login sebagai user non-root.

Siapkan folder kerja:

    praktikum/week4-proses-user/

2.Eksperimen 1 – Identitas User Jalankan perintah berikut:

    whoami
    id
    groups
Jelaskan setiap output dan fungsinya.

Buat user baru (jika memiliki izin sudo):

    sudo adduser praktikan
    sudo passwd praktikan
Uji login ke user baru.

3.Eksperimen 2 – Monitoring Proses Jalankan:

    ps aux | head -10
    top -n 1
Jelaskan kolom penting seperti PID, USER, %CPU, %MEM, COMMAND.

Simpan tangkapan layar top ke:

    praktikum/week4-proses-user/screenshots/top.png
3.Eksperimen 3 – Kontrol Proses

Jalankan program latar belakang:

    sleep 1000 &
    ps aux | grep sleep
Catat PID proses sleep.
Hentikan proses:

    kill <PID>
Pastikan proses telah berhenti dengan ps aux | grep sleep.

4.Eksperimen 4 – Analisis Hierarki Proses Jalankan:

    pstree -p | head -20
Amati hierarki proses dan identifikasi proses induk (init/systemd).

Catat hasilnya dalam laporan.
Commit & Push

    git add .
    git commit -m "Minggu 4 - Manajemen Proses & User"
    git push origin main


---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
```bash
whoami
id
groups

ps aux | head -10
top -n 1

sleep 1000 &
ps aux | grep sleep

pstree -p | head -20
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

---

## Quiz
1. [Pertanyaan 1]  
   **Jawaban:**  
2. [Pertanyaan 2]  
   **Jawaban:**  
3. [Pertanyaan 3]  
   **Jawaban:**  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
