# A3. Batasan Sistem

Penanggung jawab: Ariel Satyawan Syarah
| Kategori | Batasan Sistem | Dampak terhadap Arsitektur |
|---|---|---|
| Teknologi | Sistem harus terintegrasi dengan database presensi utama UMI dan menggunakan cloud storage untuk menyimpan dokumen bukti izin atau sakit. | Arsitektur perlu menyediakan modul integrasi database dan penyimpanan dokumen agar data dapat terhubung dengan baik. |
| Teknologi | Sistem harus dapat diakses melalui antarmuka web atau mobile oleh mahasiswa dan dosen. | Arsitektur harus mendukung tampilan yang responsif agar sistem dapat digunakan melalui komputer maupun ponsel. |
| Bisnis | Pengajuan izin dan sakit harus mengikuti aturan kampus, termasuk persyaratan dokumen dan proses verifikasi oleh dosen. | Arsitektur perlu menyediakan validasi pengajuan serta alur persetujuan atau penolakan oleh dosen. |
| Bisnis | Data izin dan sakit harus sesuai dengan aturan presensi mahasiswa, terutama dalam perhitungan persentase kehadiran sebagai syarat mengikuti ujian akhir. | Modul izin harus terintegrasi dengan modul presensi agar perubahan status tercatat secara akurat. |
| Operasional | Sistem dikembangkan secara bertahap selama semester berjalan, dimulai dari pengajuan berkas hingga sinkronisasi dengan presensi. | Arsitektur perlu dibuat modular agar setiap fitur dapat dikembangkan dan diuji secara bertahap. |
| Operasional | Sistem harus dapat digunakan oleh mahasiswa dan dosen dengan mudah serta menjaga kerahasiaan dokumen medis mahasiswa. | Arsitektur perlu menerapkan pengaturan hak akses dan pengamanan dokumen agar hanya pihak yang berwenang dapat melihatnya. |