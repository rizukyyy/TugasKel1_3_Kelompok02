# B3. Tiga Struktur Desain

## 1. Struktur Modul (Module Structure)

Struktur modul menggambarkan pembagian sistem menjadi beberapa lapisan yang memiliki fungsi dan tanggung jawab masing-masing. Pada sistem pengajuan izin dan sakit kampus, struktur modul dibagi menjadi tiga lapisan utama, yaitu lapisan tampilan, lapisan logika, dan lapisan data.

### Diagram Struktur Modul

![Diagram Struktur Modul](diagram/B3-Strukturmodul.drawio.png)

### Penjelasan

**A. Lapisan Tampilan (Presentation Layer)**

Lapisan tampilan merupakan bagian yang berinteraksi langsung dengan pengguna. Lapisan ini terdiri dari:

1. **Antarmuka Persetujuan:** Digunakan untuk memberikan persetujuan atau penolakan terhadap pengajuan izin dan sakit.
2. **Antarmuka Status dan Riwayat:** Digunakan untuk melihat status serta riwayat pengajuan.
3. **Antarmuka Pengajuan:** Digunakan pengguna untuk mengajukan izin atau sakit.

**B. Lapisan Logika (Logic Layer)**

Lapisan logika bertugas mengatur proses dan aturan bisnis sistem. Lapisan ini terdiri dari:

1. **Alur Persetujuan:** Mengatur proses persetujuan pengajuan.
2. **Pengelola Pengajuan:** Mengelola data pengajuan yang masuk.
3. **Pencatat Presensi:** Menghubungkan pengajuan izin atau sakit dengan sistem presensi.
4. **Notifikasi:** Mengirimkan pemberitahuan kepada pengguna.
5. **Validasi Pengajuan:** Memeriksa kelengkapan dan kesesuaian data pengajuan.
6. **Pengelola Bukti:** Mengelola dokumen atau bukti pendukung pengajuan.

**C. Lapisan Data (Data Layer)**

Lapisan data bertugas mengelola penyimpanan dan pengaksesan informasi. Lapisan ini terdiri dari:

1. **Akses Data Presensi:** Mengakses data kehadiran pengguna.
2. **Akses Data Izin:** Mengelola data pengajuan izin dan sakit.
3. **Penyimpanan Berkas:** Menyimpan dan mengambil dokumen bukti pengajuan.

Dengan pembagian tersebut, setiap lapisan memiliki tanggung jawab yang jelas sehingga sistem lebih terstruktur dan mudah dikembangkan maupun dipelihara.

---

## 2. Struktur Komponen dan Konektor (Component and Connector / C&C)

Struktur komponen dan konektor menggambarkan komponen-komponen yang membentuk sistem serta hubungan komunikasi di antara komponen tersebut. Sistem pengajuan izin dan sakit kampus terdiri dari beberapa komponen yang saling terhubung untuk menjalankan proses pengajuan hingga pencatatan presensi.

### Diagram Struktur Komponen dan Konektor (C&C)

![Diagram Struktur C\&C](diagram/B3-StrukturC\&C.drawio.png)

### Penjelasan

**A. Komponen Utama**

1. **Browser Pengguna:** Media yang digunakan pengguna untuk mengakses aplikasi.
2. **Server Web dan API:** Menerima permintaan pengguna dan mengelola komunikasi dengan komponen lainnya.
3. **Penyimpanan Berkas Bukti:** Menyimpan dokumen pendukung pengajuan.
4. **Basis Data Izin dan Sakit:** Menyimpan informasi pengajuan dan status persetujuan.
5. **Antrean Pesan:** Menampung pesan pengajuan yang telah disetujui untuk diproses lebih lanjut.
6. **Worker Pencatatan Presensi:** Memproses pencatatan izin atau sakit pada sistem presensi.
7. **Worker Notifikasi:** Memproses pengiriman pemberitahuan kepada pengguna.
8. **Layanan Presensi:** Mengelola perubahan data kehadiran pengguna.
9. **Basis Data Presensi:** Menyimpan informasi kehadiran pengguna.
10. **Layanan Email dan Notifikasi:** Mengirimkan pemberitahuan melalui email atau layanan notifikasi lainnya.

**B. Konektor atau Hubungan Antar-Komponen**

1. **HTTPS:** Menghubungkan browser pengguna dengan server web dan API.
2. **Akses Berkas:** Menghubungkan server aplikasi dengan penyimpanan berkas bukti.
3. **SQL:** Digunakan untuk menyimpan, membaca, dan memperbarui data pada basis data izin dan sakit.
4. **Kirim Pesan:** Mengirimkan informasi pengajuan yang telah disetujui ke antrean pesan.
5. **Konsumsi Pesan:** Menghubungkan antrean pesan dengan worker pencatatan presensi dan worker notifikasi.
6. **HTTPS API:** Menghubungkan worker pencatatan presensi dengan layanan presensi.
7. **SMTP atau API:** Menghubungkan worker notifikasi dengan layanan email dan notifikasi.

Dengan adanya komponen dan konektor tersebut, setiap bagian sistem dapat berkomunikasi secara terintegrasi. Penggunaan antrean pesan memungkinkan proses pencatatan presensi dan pengiriman notifikasi berjalan secara terpisah dari proses utama pengajuan.

---

## 3. Struktur Alokasi (Allocation Structure)

Struktur alokasi menggambarkan penempatan komponen perangkat lunak pada perangkat pengguna, server, infrastruktur kampus, serta pembagian tanggung jawab tim pengembang.

### Diagram Struktur Alokasi

![Diagram Struktur Alokasi](diagram/B3-Struktur-alokasi.drawio.png)

### Penjelasan

**A. Perangkat Pengguna**

Perangkat pengguna merupakan tempat pengguna mengakses sistem melalui browser. Komunikasi dengan server aplikasi dilakukan menggunakan protokol HTTPS.

**B. Server Aplikasi - Cloud Kampus**

Server aplikasi merupakan pusat pemrosesan sistem yang terdiri dari:

1. **Server Web dan API:** Menerima permintaan pengguna dan mengatur komunikasi dengan komponen lainnya.
2. **Antrean Pesan:** Menampung pesan pengajuan yang telah disetujui.
3. **Worker Pencatatan Presensi:** Memproses pencatatan izin atau sakit pada sistem presensi.
4. **Worker Notifikasi:** Memproses pengiriman pemberitahuan kepada pengguna.

**C. Server Data Kampus**

Server data kampus berfungsi sebagai tempat penyimpanan informasi utama sistem, yang terdiri dari:

1. **Penyimpanan Berkas Bukti:** Menyimpan dokumen pendukung seperti surat izin atau surat keterangan sakit.
2. **Basis Data Izin dan Sakit:** Menyimpan data pengajuan serta status persetujuan.

**D. Server Presensi Kampus**

Server presensi kampus digunakan untuk mengelola data kehadiran pengguna. Komponen di dalamnya terdiri dari:

1. **Layanan Presensi:** Menerima permintaan dari worker pencatatan presensi melalui HTTPS API.
2. **Basis Data Presensi:** Menyimpan data kehadiran yang telah diperbarui.

**E. Layanan Eksternal**

Layanan eksternal merupakan layanan pendukung dari luar infrastruktur utama kampus, yaitu layanan email dan notifikasi. Layanan ini digunakan untuk mengirimkan informasi mengenai status pengajuan kepada pengguna melalui SMTP atau API.

**F. Pembagian Tugas Tim Pengembang**

Pengembangan sistem dibagi menjadi empat tim berdasarkan tanggung jawab masing-masing:

1. **Tim 1 - Antarmuka:** Bertanggung jawab mengembangkan antarmuka pengajuan, antarmuka persetujuan, serta antarmuka status dan riwayat.
2. **Tim 2 - Pengelola Pengajuan:** Bertanggung jawab mengembangkan validasi pengajuan dan pengelolaan bukti.
3. **Tim 3 - Alur Persetujuan:** Bertanggung jawab mengembangkan alur persetujuan, pencatatan presensi, dan notifikasi.
4. **Tim 4 - Akses Data:** Bertanggung jawab mengembangkan akses data izin, akses data presensi, dan penyimpanan berkas.

Struktur alokasi ini bertujuan agar setiap komponen ditempatkan sesuai dengan fungsi dan kebutuhannya. Pembagian tanggung jawab tim juga membantu proses pengembangan menjadi lebih terorganisasi.

---

## Kesimpulan

Berdasarkan ketiga struktur desain tersebut, sistem pengajuan izin dan sakit kampus dirancang menggunakan pendekatan berlapis dan komponen yang saling terintegrasi.

1. **Struktur Modul** menjelaskan pembagian sistem menjadi lapisan tampilan, lapisan logika, dan lapisan data.
2. **Struktur Komponen dan Konektor (C&C)** menjelaskan komponen sistem serta mekanisme komunikasi antar-komponen menggunakan HTTPS, SQL, antrean pesan, dan SMTP/API.
3. **Struktur Alokasi** menjelaskan penempatan komponen pada perangkat pengguna, server aplikasi, server data kampus, server presensi, serta layanan eksternal dan pembagian tanggung jawab tim pengembang.

Ketiga struktur tersebut saling melengkapi untuk menggambarkan rancangan sistem mulai dari pembagian fungsi, hubungan komunikasi, hingga penempatan komponen dan tanggung jawab pengembangannya.
