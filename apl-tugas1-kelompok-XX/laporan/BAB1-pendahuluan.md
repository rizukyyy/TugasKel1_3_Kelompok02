# BAB I. Pendahuluan

<!-- Gambaran subsistem dan layanan inti yang ditugaskan, ruang lingkup, dan sumber data. -->
<!-- Penanggung jawab: Zulfajrin -->

# BAB I. PENDAHULUAN

## 1.1 Gambaran Layanan Inti

Layanan izin dan sakit mahasiswa merupakan layanan yang digunakan untuk memfasilitasi mahasiswa dalam mengajukan izin ketidakhadiran karena keperluan tertentu atau kondisi sakit. Layanan ini mencakup proses pengajuan izin, pengunggahan bukti pendukung, pemeriksaan pengajuan oleh pihak yang berwenang, pemberian persetujuan atau penolakan, serta pencatatan status ketidakhadiran ke dalam sistem presensi.

Melalui layanan ini, mahasiswa dapat mengajukan izin secara lebih terstruktur. Dosen atau pihak yang berwenang dapat memeriksa pengajuan beserta bukti pendukung sebelum memberikan keputusan. Status pengajuan juga dapat dipantau sehingga proses pencatatan presensi menjadi lebih jelas dan mengurangi risiko kesalahan pencatatan.

Dalam perancangan arsitektur perangkat lunak, layanan ini perlu memperhatikan keamanan data mahasiswa, kerahasiaan dokumen bukti sakit, ketepatan proses persetujuan, dan konsistensi data antara pengajuan izin dengan catatan presensi.

Secara umum, layanan ini memiliki empat proses utama yang saling berkaitan, yaitu pengajuan izin atau sakit, pemeriksaan bukti pendukung, persetujuan pengajuan, dan pencatatan ke sistem presensi.

## 1.2 Ruang Lingkup (3–5 Kasus Penggunaan)

Ruang lingkup layanan izin dan sakit mahasiswa difokuskan pada proses pengajuan ketidakhadiran, pemeriksaan bukti pendukung, persetujuan pengajuan, serta pencatatan status ke dalam sistem presensi. Pembahasan mencakup lima kasus penggunaan utama berikut.

| No. | Kasus Penggunaan | Aktor | Deskripsi |
|---|---|---|---|
| 1 | Pengajuan Izin atau Sakit | Mahasiswa | Mahasiswa mengisi dan mengirim formulir pengajuan izin atau sakit dengan mencantumkan tanggal, alasan, dan keterangan ketidakhadiran. |
| 2 | Pengunggahan Bukti Pendukung | Mahasiswa | Mahasiswa mengunggah dokumen pendukung, seperti surat keterangan sakit, resep, atau surat izin dalam bentuk foto maupun PDF. |
| 3 | Verifikasi dan Persetujuan Pengajuan | Dosen | Dosen memeriksa informasi dan bukti pendukung, kemudian memberikan persetujuan atau penolakan terhadap pengajuan mahasiswa. |
| 4 | Melihat Status Pengajuan | Mahasiswa | Mahasiswa melihat perkembangan status pengajuan, seperti menunggu verifikasi, disetujui, atau ditolak beserta alasan penolakan jika ada. |
| 5 | Pencatatan ke Sistem Presensi | Admin Akademik dan Operator Akademik | Pengajuan yang telah disetujui dicatat atau diteruskan ke sistem presensi agar status ketidakhadiran mahasiswa sesuai dengan keputusan yang diberikan. |

Ruang lingkup ini berfokus pada pengelolaan pengajuan izin dan sakit hingga pencatatannya ke sistem presensi. Layanan ini tidak mencakup diagnosis medis, penerbitan surat keterangan sakit, maupun pengelolaan keseluruhan sistem akademik kampus.

## 1.3 Sumber Data

Sumber data dalam analisis layanan izin dan sakit mahasiswa diperoleh dari beberapa pihak yang berkaitan langsung dengan proses pengajuan, pemeriksaan, persetujuan, dan pencatatan presensi. Pengumpulan informasi dilakukan berdasarkan peran masing-masing pihak untuk mengetahui kebutuhan, kendala, dan harapan terhadap sistem yang akan dirancang.

### 1. Mahasiswa

| No. | Pertanyaan | Jawaban |
|---|---|---|
| 1 | Bagaimana cara Anda mengajukan izin atau sakit saat ini, dan kendala apa yang paling sering Anda alami? | Saya mengajukan lewat WhatsApp ke dosen atau menyerahkan surat langsung. Kendalanya, pesan sering lambat dibalas, surat bisa hilang, dan status izin tidak jelas. |
| 2 | Bukti pendukung apa saja yang biasanya Anda siapkan, dan dalam format apa Anda lebih mudah mengunggahnya? | Biasanya surat dokter, resep, atau surat dari orang tua. Saya lebih mudah mengunggah dalam bentuk foto (JPG/PNG) atau PDF dari ponsel. |
| 3 | Informasi apa yang ingin Anda lihat pada status pengajuan, dan bagaimana Anda ingin diberi tahu hasilnya? | Saya ingin melihat status (menunggu, disetujui, ditolak), tanggal pengajuan, dan alasan jika ditolak. Pemberitahuan lewat notifikasi aplikasi atau email. |

### 2. Dosen

| No. | Pertanyaan | Jawaban |
|---|---|---|
| 1 | Bagaimana proses Anda memeriksa pengajuan izin atau sakit mahasiswa saat ini, dan berapa lama waktu yang dibutuhkan? | Pengajuan masuk lewat pesan pribadi atau surat fisik, lalu diperiksa satu per satu. Butuh sekitar 5 sampai 10 menit per pengajuan dan sering tertunda karena tercampur pesan lain. |
| 2 | Apa saja kriteria untuk menyetujui atau menolak pengajuan, dan bukti apa yang wajib dilampirkan? | Kriterianya alasan jelas, tanggal sesuai jadwal kuliah, dan bukti lengkap. Sakit wajib surat dokter, izin wajib surat resmi atau dokumen pendukung. |
| 3 | Fitur apa yang paling membantu Anda dalam menyetujui pengajuan? | Notifikasi pengajuan baru, daftar antrean terurut tanggal, dan persetujuan massal. Bukti juga bisa dilihat langsung tanpa diunduh. |

### 3. Admin Akademik

| No. | Pertanyaan | Jawaban |
|---|---|---|
| 1 | Bagaimana alur pengelolaan data kehadiran saat ini, dan di bagian mana sering terjadi kesalahan atau data tidak lengkap? | Data dikumpulkan dari dosen lewat lembar absensi atau Excel, lalu diinput manual. Kesalahan sering terjadi pada input ganda, status izin atau sakit tidak tercatat, dan data terlambat dikirim. |
| 2 | Apa saja yang Anda periksa untuk memastikan kelengkapan data pengajuan izin atau sakit sebelum masuk laporan? | Saya memeriksa NIM dan nama, tanggal dan mata kuliah, alasan, bukti pendukung, serta status persetujuan dosen. |
| 3 | Jenis laporan kehadiran apa yang Anda butuhkan, dan dalam format apa? | Laporan per mahasiswa, per mata kuliah, dan per periode (bulanan atau semester) dalam format Excel dan PDF, berisi jumlah hadir, izin, sakit, dan alpa. |

### 4. Operator Akademik

| No. | Pertanyaan | Jawaban |
|---|---|---|
| 1 | Data akademik apa saja yang Anda kelola sehari-hari, dan bagaimana keterkaitannya dengan data kehadiran? | Saya mengelola data mahasiswa, jadwal, mata kuliah, dan nilai. Kehadiran terkait langsung karena menjadi syarat ujian, misalnya minimal kehadiran 75%. |
| 2 | Bagaimana cara Anda membuat rekapitulasi kehadiran saat ini, dan bagian mana yang paling lama atau rawan salah? | Rekap dibuat manual di Excel dari data beberapa dosen. Paling lama saat menyamakan format dan menghitung ulang, paling rawan saat mencocokkan data izin atau sakit dengan absensi. |
| 3 | Apa yang Anda harapkan dari sistem baru agar rekapitulasi lebih cepat dan akurat? | Rekap otomatis yang terhubung dengan pengajuan yang disetujui, filter per kelas atau periode, ekspor ke Excel, dan peringatan untuk mahasiswa yang mendekati batas ketidakhadiran. |

### 5. Tim Pengembangan Sistem

| No. | Pertanyaan | Jawaban |
|---|---|---|
| 1 | Teknologi dan sistem apa yang perlu diintegrasikan? | Sistem informasi akademik, basis data MySQL atau PostgreSQL, dan aplikasi berbasis web. |
| 2 | Bagaimana kebutuhan keamanan dan hak akses? | Kata sandi harus disimpan secara aman menggunakan metode hashing, hak akses disesuaikan dengan peran pengguna, pembatasan akses file, dan pencatatan aktivitas sistem. |
| 3 | Bagaimana rencana pemeliharaan sistem? | Pemeliharaan dilakukan melalui log otomatis, backup harian, serta penyampaian keluhan melalui formulir atau email. |

Berdasarkan sumber data tersebut, dapat diketahui bahwa layanan izin dan sakit mahasiswa membutuhkan proses pengajuan yang mudah, pemeriksaan bukti yang terstruktur, pemberian keputusan yang jelas, serta integrasi dengan sistem presensi. Selain itu, sistem perlu memperhatikan keamanan data, kemudahan penggunaan, ketepatan pencatatan, dan pemeliharaan sistem.