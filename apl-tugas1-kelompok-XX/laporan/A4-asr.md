# A4. Kebutuhan Signifikan (ASR)

Penanggung jawab: Airil Nasbi
Subsistem: Aplikasi KRS Online

ASR-1 (Atribut Kualitas: Kinerja dan Skalabilitas)
Kebutuhan : Sistem harus tetap responsif (95% permintaan selesai
            dalam waktu kurang dari 3 detik) saat 5.000 mahasiswa
            mengakses dan mengisi KRS secara bersamaan pada hari
            pertama periode pengisian.
Alasan    : Beban akses sangat terpusat pada waktu yang singkat
            (lonjakan beban/peak load). Kebutuhan ini memaksa
            arsitektur memakai pemisahan lapisan aplikasi dan
            basis data, caching, load balancing, serta
            kemungkinan antrean permintaan. Jika tidak
            dirancang sejak awal, perubahan di kemudian hari
            akan sangat mahal karena menyentuh seluruh struktur
            sistem.

ASR-2 (Atribut Kualitas: Ketersediaan / Availability)
Kebutuhan : Sistem harus tersedia minimal 99,5% selama periode
            pengisian KRS, dan tidak boleh mati lebih dari 15
            menit berturut-turut pada jam akademik.
Alasan    : Pengisian KRS dibatasi jadwal akademik, sehingga
            gangguan layanan membuat mahasiswa gagal mendaftar
            mata kuliah dan memicu keluhan massal. Kebutuhan ini
            mempengaruhi keputusan redundansi server, replikasi
            basis data, mekanisme failover, serta strategi
            pemantauan dan pemulihan (recovery).

ASR-3 (Atribut Kualitas: Keamanan)
Kebutuhan : Hanya mahasiswa yang terautentikasi yang dapat
            mengubah KRS miliknya sendiri; dosen wali hanya
            dapat menyetujui KRS mahasiswa bimbingannya; semua
            perubahan KRS tercatat dalam log audit.
Alasan    : KRS adalah data akademik resmi yang berdampak pada
            biaya kuliah dan status studi. Kebutuhan ini
            mempengaruhi arsitektur autentikasi (SSO), otorisasi
            berbasis peran (RBAC), enkripsi komunikasi, dan
            pencatatan audit, yang harus ditempatkan sebagai
            komponen lintas modul, bukan ditambahkan belakangan.

ASR-4 (Fungsional: Validasi Aturan Akademik)
Kebutuhan : Sistem harus memvalidasi otomatis prasyarat mata
            kuliah, batas SKS berdasarkan IPS, kuota kelas, dan
            bentrok jadwal pada saat mahasiswa menyimpan KRS.
Alasan    : Validasi ini harus konsisten dan atomik, terutama
            untuk kuota kelas yang diperebutkan banyak mahasiswa
            sekaligus. Kebutuhan ini mempengaruhi desain modul
            aturan bisnis yang terpisah (agar mudah diubah saat
            kebijakan berubah) serta penanganan transaksi dan
            konkurensi pada basis data.

ASR-5 (Batasan / Constraint: Integrasi Sistem Akademik)
Kebutuhan : KRS Online wajib terintegrasi dengan Sistem Informasi
            Akademik (SIAKAD) kampus yang sudah ada, termasuk data
            mahasiswa, jadwal kuliah, dan data keuangan (status
            pembayaran UKT).
Alasan    : Sistem tidak dapat berdiri sendiri dan harus
            mengikuti format data serta antarmuka sistem lama.
            Batasan ini mempengaruhi pemilihan gaya integrasi
            (API/adapter), kebutuhan lapisan anti-korupsi, dan
            ketahanan sistem bila SIAKAD lambat atau tidak
            tersedia.


