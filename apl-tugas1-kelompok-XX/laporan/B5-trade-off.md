# B5. Analisis Trade-off

<!-- Penanggung jawab: Airil nasbi
Subsistem: Aplikasi KRS Online

PASANGAN 1: KEAMANAN vs KINERJA

Penjelasan dampak:
Keamanan yang ketat (autentikasi berlapis, enkripsi, pemeriksaan
otorisasi pada setiap permintaan, dan pencatatan log audit)
menambah proses pada setiap permintaan sehingga waktu respons
bertambah. Pada saat 5.000 mahasiswa mengakses bersamaan,
tambahan beban ini bisa membuat sistem melewati batas waktu
respons 3 detik. Sebaliknya, jika kinerja dikejar dengan
mengurangi pemeriksaan keamanan (misalnya sesi login dibuat
sangat lama atau log dimatikan), risiko pengubahan KRS oleh pihak
tidak berwenang meningkat.

Karakteristik yang didahulukan: KEAMANAN

Alasan:
KRS adalah data akademik resmi, sehingga kebocoran atau
manipulasi data berdampak serius (hukum, reputasi kampus, dan
keadilan bagi mahasiswa) dan sulit dipulihkan. Sebaliknya, masalah
kinerja bisa diatasi dengan menambah sumber daya (scaling), caching
data non-sensitif, dan optimasi, tanpa mengorbankan keamanan.
Jadi, kinerja dicapai dengan cara yang tidak melemahkan keamanan.

PASANGAN 2: KETERSEDIAAN vs KONSISTENSI DATA

Penjelasan dampak:
Untuk menjaga ketersediaan tinggi, sistem memakai replika basis
data dan cache. Namun replika bisa tertinggal dari data utama,
sehingga sisa kuota kelas yang ditampilkan bisa tidak akurat dan
dua mahasiswa dapat sama-sama berhasil mengambil kursi terakhir.
Jika konsistensi dijaga ketat (semua penulisan harus
tersinkronisasi dan dikunci), sistem menjadi lebih lambat dan
dapat menolak permintaan ketika sebagian komponen bermasalah,
sehingga ketersediaan turun.

Karakteristik yang didahulukan: KONSISTENSI DATA (khusus proses
penyimpanan KRS dan pengurangan kuota), sedangkan ketersediaan
tetap diutamakan untuk fungsi baca seperti melihat jadwal dan
daftar mata kuliah.

Alasan:
Kuota kelas dan data KRS yang salah menimbulkan masalah nyata
(kelas melebihi kapasitas, KRS tidak sah) yang sulit diperbaiki
setelah terjadi. Menolak sementara satu transaksi lebih dapat
diterima daripada menyimpan data yang keliru. Untuk fungsi
yang tidak mengubah data, kondisi data yang sedikit tertinggal
masih dapat ditoleransi sehingga ketersediaan tetap terjaga.

PASANGAN 3 (TAMBAHAN): KEMUDAHAN PERUBAHAN (MODIFIABILITY)
                       vs KINERJA

Penjelasan dampak:
Memisahkan aturan akademik ke modul tersendiri dan memakai lapisan
integrasi (adapter) memudahkan perubahan kebijakan, tetapi
menambah lapisan pemanggilan yang sedikit memperlambat proses.
Sebaliknya, menggabungkan semua logika langsung ke basis data
lebih cepat, namun setiap perubahan aturan menjadi sulit dan
berisiko.

Karakteristik yang didahulukan: KEMUDAHAN PERUBAHAN

Alasan:
Aturan KRS (batas SKS, prasyarat) sering berubah setiap
semester atau kurikulum. Selisih kinerja akibat lapisan tambahan
relatif kecil dan bisa dikompensasi dengan caching, sedangkan
biaya perubahan pada desain yang kaku akan terus berulang.

