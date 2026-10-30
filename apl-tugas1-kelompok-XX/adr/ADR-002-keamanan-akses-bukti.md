# ADR-002: Penerapan Pembatasan Hak Akses dan Pemisahan Penyimpanan Bukti Izin dan Sakit

- **Status:** Diusulkan
- **Tanggal:** 31-10-2026
- **Pengambil keputusan:** Andi Muhammad Dzaki Idrus

## Context

Layanan izin dan sakit mengelola informasi pengajuan mahasiswa beserta bukti pendukung yang diunggah. Informasi tersebut perlu dilindungi agar hanya dapat diakses oleh pengguna yang memiliki kewenangan.

Mahasiswa hanya diperbolehkan mengajukan dan melihat pengajuan miliknya sendiri, sedangkan pihak penyetuju memiliki kewenangan untuk memeriksa bukti serta memberikan persetujuan atau penolakan terhadap pengajuan. Petugas presensi memiliki akses sesuai tanggung jawabnya dalam memeriksa pencatatan izin atau sakit.

Selain itu, berkas bukti izin dan sakit perlu dikelola secara terpisah dari data pengajuan agar penyimpanan dan pengambilan dokumen dapat dilakukan secara terstruktur.

## Decision

Kami akan menerapkan Role-Based Access Control (RBAC) untuk membatasi hak akses berdasarkan peran mahasiswa, pihak penyetuju, dan petugas presensi.

Setiap permintaan akses akan diperiksa melalui Server Web dan API untuk memastikan pengguna memiliki kewenangan terhadap data yang diminta.

Kami juga akan memisahkan penyimpanan berkas bukti dari Basis Data Izin dan Sakit. Informasi pengajuan dan statusnya disimpan dalam basis data, sedangkan dokumen bukti disimpan pada Penyimpanan Berkas Bukti.

Pengambilan berkas dilakukan melalui Server Web dan API setelah pemeriksaan hak akses pengguna.

## Consequences

**Dampak positif:**
- Membatasi akses pengajuan sesuai kewenangan masing-masing pengguna.
- Melindungi kerahasiaan berkas bukti izin dan sakit.
- Memisahkan pengelolaan data pengajuan dengan penyimpanan berkas.
- Memudahkan pengelolaan dan pengambilan kembali bukti pendukung.

**Dampak negatif:**
- Membutuhkan pemeriksaan hak akses pada setiap permintaan pengguna.
- Menambah kompleksitas pengelolaan peran dan kewenangan.
- Membutuhkan pengelolaan penyimpanan serta pencadangan berkas secara terpisah.

**Trade-off:** Keamanan dan kerahasiaan data pengajuan serta bukti diprioritaskan meskipun pemeriksaan hak akses menambah proses pada setiap permintaan pengguna.

## Compliance

- Menguji hak akses berdasarkan peran mahasiswa, pihak penyetuju, dan petugas presensi.
- Memastikan mahasiswa hanya dapat melihat pengajuan miliknya sendiri.
- Memastikan pihak penyetuju hanya dapat mengakses pengajuan sesuai kewenangannya.
- Memastikan pengguna tanpa hak akses tidak dapat mengambil berkas bukti.
- Melakukan pemeriksaan kode untuk memastikan otorisasi diterapkan pada sisi server.
- Memastikan pemisahan data pengajuan dan penyimpanan berkas berjalan sesuai rancangan.
