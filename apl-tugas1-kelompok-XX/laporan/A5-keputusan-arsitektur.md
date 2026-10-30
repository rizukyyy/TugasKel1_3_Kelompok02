# A5. Keputusan Arsitektur dan ADR

**Penanggung jawab:** Andi Muhammad Dzaki Idrus

Bagian ini menjelaskan keputusan arsitektur untuk layanan izin dan sakit yang mencakup pengajuan, bukti, persetujuan, dan pencatatan ke presensi.

## 1. Ringkasan ADR-001: Penerapan Antrean Pesan dan Worker untuk Pencatatan Presensi

- **Status:** Diusulkan
- **ASR terkait:** ASR-1 (Keandalan dan Integrasi Pencatatan Presensi)
- **ADR lengkap:** [ADR-001-antrean-pesan-pencatatan-presensi.md](../adr/ADR-001-antrean-pesan-pencatatan-presensi.md)

## 2. Ringkasan ADR-002: Penerapan Pembatasan Hak Akses dan Pemisahan Penyimpanan Bukti

- **Status:** Diusulkan
- **ASR terkait:** ASR-2 (Keamanan dan Kerahasiaan Data Pengajuan serta Bukti)
- **ADR lengkap:** [ADR-002-keamanan-akses-bukti.md](../adr/ADR-002-keamanan-akses-bukti.md)

## 3. Rencana Komunikasi Keputusan Arsitektur

1. **Lokasi dokumentasi:** ADR lengkap disimpan pada folder `adr/` dalam repository GitHub kelompok, sedangkan ringkasannya dicantumkan pada file A5.
2. **Penerima informasi:** Seluruh anggota kelompok, terutama anggota yang bertanggung jawab terhadap modul pengajuan, persetujuan, pencatatan presensi, dan pengelolaan bukti.
3. **Mekanisme komunikasi:** Keputusan dibahas bersama dan setiap perubahan didokumentasikan melalui pembaruan ADR serta riwayat commit GitHub.
4. **Perubahan keputusan:** Jika terdapat keputusan baru yang menggantikan keputusan sebelumnya, status ADR lama diperbarui dan dibuat ADR pengganti.

### Pencegahan Antipattern Komunikasi

- **Covering Your Assets:** Setiap keputusan didokumentasikan dengan alasan, alternatif, serta konsekuensinya secara terbuka.
- **Groundhog Day:** Anggota kelompok memeriksa ADR yang sudah tersedia sebelum membahas atau mengambil keputusan baru.
- **Email-Driven Architecture:** Keputusan penting harus tercatat dalam ADR pada repository, bukan hanya disampaikan melalui pesan pribadi atau email.

