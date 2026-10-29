# B1. Identifikasi dan Klasifikasi Karakteristik

<!-- Penanggung jawab: ZULFAJRIN -->


## 1. Identifikasi Kandidat Karakteristik

Pada perancangan arsitektur perangkat lunak untuk layanan izin dan sakit mahasiswa, diperlukan identifikasi karakteristik yang dapat memengaruhi kualitas dan struktur sistem. Layanan ini mencakup pengajuan izin, pengunggahan bukti pendukung, pemeriksaan dan persetujuan, serta pencatatan status izin ke dalam sistem presensi.

Berdasarkan kebutuhan layanan tersebut, diidentifikasi sepuluh kandidat karakteristik yang relevan. Kandidat-kandidat ini dikelompokkan berdasarkan kategori arsitektur, yaitu operasional, struktural, dan lintas sektor, serta sifatnya, yaitu eksplisit atau implisit.

| No. | Kandidat Karakteristik | Kategori | Sifat | Alasan |
|---|---|---|---|---|
| 1 | Kinerja (*Performance*) | Operasional | Eksplisit | Sistem perlu memberikan respons yang memadai ketika mahasiswa mengajukan izin dan memeriksa status pengajuannya. |
| 2 | Keamanan (*Security*) | Lintas sektor | Eksplisit | Sistem perlu membatasi akses terhadap pengajuan, keputusan persetujuan, dan dokumen pendukung berdasarkan kewenangan pengguna. |
| 3 | Privasi (*Privacy*) | Lintas sektor | Implisit | Dokumen pendukung izin atau sakit dapat memuat informasi pribadi mahasiswa yang harus dilindungi. |
| 4 | Integritas Data (*Data Integrity*) | Lintas sektor | Eksplisit | Informasi pengajuan, hasil persetujuan, dan pencatatan presensi harus konsisten serta tidak mengalami perubahan yang tidak sah. |
| 5 | Ketersediaan (*Availability*) | Operasional | Eksplisit | Layanan perlu dapat diakses pengguna ketika dibutuhkan, sesuai jadwal operasional sistem. |
| 6 | Kemudahan Penggunaan (*Usability*) | Operasional | Implisit | Mahasiswa dan dosen membutuhkan alur pengajuan, pemeriksaan, serta pemantauan status yang mudah dipahami. |
| 7 | Kemudahan Pemeliharaan (*Maintainability*) | Struktural | Eksplisit | Struktur sistem perlu mendukung perbaikan dan perubahan aturan pengajuan izin tanpa mengganggu keseluruhan layanan. |
| 8 | Interoperabilitas (*Interoperability*) | Struktural | Eksplisit | Layanan perlu mendukung pertukaran data dengan sistem presensi agar pengajuan yang disetujui dapat dicatat sesuai aturan. |
| 9 | Auditabilitas (*Auditability*) | Lintas sektor | Eksplisit | Riwayat pengajuan, keputusan, dan perubahan status perlu dapat ditelusuri untuk mendukung pemeriksaan apabila terjadi kesalahan. |
| 10 | Portabilitas (*Portability*) | Struktural | Implisit | Rancangan sebaiknya mempertimbangkan kemungkinan penerapan atau pemindahan layanan ke lingkungan infrastruktur yang berbeda. |

**Keterangan:**
- **Operasional:** berkaitan dengan perilaku atau kualitas sistem ketika dijalankan.
- **Struktural:** berkaitan dengan susunan komponen, hubungan antarmodul, dan rancangan arsitektur.
- **Lintas sektor:** berkaitan dengan karakteristik yang memengaruhi beberapa komponen atau lapisan sistem.
- **Eksplisit:** dinyatakan secara langsung sebagai kebutuhan atau target dalam rancangan.
- **Implisit:** disimpulkan dari konteks penggunaan dan kebutuhan layanan meskipun tidak dinyatakan secara langsung.

Klasifikasi di atas merupakan usulan awal berdasarkan konteks layanan dan perlu disesuaikan dengan definisi kategori yang digunakan dalam materi perkuliahan.

## 2. Pemilihan Tiga Karakteristik Pendorong

Dari sepuluh kandidat yang telah diidentifikasi, dipilih tiga karakteristik yang paling berpengaruh terhadap keputusan arsitektur perangkat lunak, yaitu keamanan dan privasi, integritas data, serta kinerja.

Pemilihan dilakukan dengan mempertimbangkan tiga ciri: pengaruh terhadap keputusan arsitektur, dampak terhadap beberapa bagian sistem, dan kemampuan untuk diuji atau diukur.

| No. | Karakteristik Pendorong | Pengaruh terhadap Keputusan Arsitektur | Dampak terhadap Sistem | Cara Pengujian atau Pengukuran |
|---|---|---|---|---|
| 1 | Keamanan dan Privasi | Memerlukan autentikasi, pembatasan hak akses, serta perlindungan dokumen pendukung. | Memengaruhi antarmuka, layanan aplikasi, penyimpanan dokumen, dan pencatatan aktivitas. | Menguji hak akses pengguna, akses dokumen oleh pihak yang tidak berwenang, dan kelengkapan catatan aktivitas. |
| 2 | Integritas Data | Memerlukan pengelolaan transaksi dan mekanisme integrasi yang menjaga konsistensi data pengajuan dengan presensi. | Memengaruhi proses pengajuan, persetujuan, penyimpanan data, dan integrasi presensi. | Menguji pengajuan duplikat, perubahan status, serta penanganan kegagalan komunikasi dengan sistem presensi. |
| 3 | Kinerja | Memengaruhi pemilihan teknologi, rancangan API, pengelolaan basis data, dan kapasitas infrastruktur. | Memengaruhi waktu respons pada proses pengajuan, pemeriksaan status, dan pengambilan data. | Mengukur waktu respons, jumlah permintaan yang dapat diproses, dan penggunaan sumber daya saat pengujian beban. |

## 3. Alasan Pemilihan Karakteristik Pendorong

### a. Keamanan dan Privasi

Keamanan dan privasi dipilih karena layanan mengelola informasi mahasiswa serta dokumen pendukung izin dan sakit. Karakteristik ini memengaruhi keputusan arsitektur melalui penerapan autentikasi, otorisasi berbasis peran, perlindungan penyimpanan dokumen, dan pencatatan aktivitas pengguna. Pengujian dapat dilakukan untuk memastikan bahwa dokumen hanya dapat diakses oleh pihak yang memiliki kewenangan.

### b. Integritas Data

Integritas data dipilih karena hasil persetujuan izin atau sakit harus dicatat secara benar pada sistem presensi. Kesalahan integrasi dapat menyebabkan ketidaksesuaian status pengajuan dengan catatan kehadiran mahasiswa. Oleh karena itu, arsitektur perlu memperhatikan konsistensi penyimpanan data, pencegahan pemrosesan ganda, dan penanganan kegagalan integrasi.

### c. Kinerja

Kinerja dipilih karena pengguna membutuhkan layanan yang memberikan respons dalam waktu yang wajar. Waktu respons yang terlalu lama dapat menghambat mahasiswa saat mengajukan izin dan dosen ketika memeriksa pengajuan. Karakteristik ini memengaruhi rancangan pengolahan permintaan, optimasi basis data, dan kapasitas infrastruktur serta dapat dinilai melalui pengujian beban.

