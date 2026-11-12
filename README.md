# WargaHub P04 – UX, RecyclerView, Fragment, dan Navigasi

Praktikum 04 • Pemrograman Mobile (PTI23043) • Dosen pengampu: Muhayat, M.IT

| | |
|---|---|
| Nama | Najib Rabbani Syarif |
| NIM | 240104040058 |
| Kelas | TI24B |
| Proyek | `WargaHubP04` • package `id.antasari.p04.wargahub` |

## Ringkasan fitur
Aplikasi Android native (Kotlin, XML Views, ViewBinding) dengan satu Activity dan tiga Fragment:

- **Beranda**: penjelasan aplikasi dan catatan bahwa data hanya contoh; tombol *Lihat Daftar Laporan*.
- **Daftar Laporan**: 15 laporan fiktif dalam `RecyclerView` (`ListAdapter` + `DiffUtil` + `ViewHolder` dengan ViewBinding), jumlah laporan, petunjuk gulir, dan tombol *Uji Daftar Kosong* / *Tampilkan Data Contoh*.
- **Rincian Laporan**: judul, kategori, status contoh, dan deskripsi sesuai ID laporan yang dipilih; tombol *Kembali ke Daftar* memakai `navigateUp()`.
- Navigasi memakai Navigation Component (3 tujuan, 2 action, argumen `laporan_id` bertipe `long`), toolbar terhubung ke `NavController`.
- Daftar kosong memiliki pesan dan aksi pemulihan; ID yang tidak ditemukan menampilkan pesan aman.

## Batas data contoh
Semua laporan adalah data fiktif yang dibentuk dari kode (`LaporanContoh`). Tidak ada database, penyimpanan permanen, permission INTERNET, atau fitur tambah laporan. Status "Simulasi" bukan status tiket layanan nyata. Data muncul kembali setelah aplikasi dimulai ulang karena dibentuk ulang dari kode, bukan karena disimpan.

## Perangkat dan versi alat
- Perangkat uji: emulator **Medium Phone API 37.0** (API 37)
- Android Gradle Plugin 9.4.1 • Gradle 9.6.0 (Gradle Wrapper bawaan)
- compileSdk 37 • minSdk 26 • targetSdk 37 • Kotlin • versi aplikasi 1.0
- Dependensi: RecyclerView 1.4.0, Fragment-ktx 1.8.9, Navigation-fragment-ktx 2.9.5, Navigation-ui-ktx 2.9.5
- Versi Android Studio: tidak dicatat

## Cara membuka dan menjalankan
1. Buka Android Studio → **Open** → pilih folder `WargaHubP04` (yang berisi `settings.gradle.kts` dan `gradlew`).
2. Tunggu Gradle Sync selesai (butuh internet pada sinkronisasi pertama). `local.properties` tidak disertakan; Android Studio akan membuatnya otomatis.
3. Pilih emulator atau perangkat (minSdk 26), lalu tekan **Run**.
4. Alternatif build dari Terminal (di root `WargaHubP04`): `.\gradlew.bat assembleDebug` (Windows) atau `./gradlew assembleDebug` (macOS/Linux).

## Isi folder pengumpulan
```
P04_240104040058_Najib_Rabbani_Syarif/
├── WargaHubP04/            # source project + Gradle Wrapper
├── README.md
├── docs/Laporan_P04.docx   # sketsa, penjelasan, matriks uji, uji teman, temuan, refleksi
└── screenshots/            # bukti (S01–S14, T06, T07, T15, E1–E3)
```

## Ringkasan hasil uji
Hasil lengkap dan bukti ada di `docs/Laporan_P04.docx`.

| Skenario | Status |
|---|---|
| T01–T11, T14, T15 | Lulus |
| T12 Font besar dan landscape | Lulus untuk Daftar dan Daftar kosong; Beranda dan Rincian dengan font besar belum dicatat |
| T13 TalkBack | **Belum Diuji** (keterbatasan dan rencana uji alternatif ada di laporan) |
| T16 ID tidak ditemukan | Lulus (dengan perubahan sementara `-99L`, sudah dikembalikan menjadi `laporan.id`) |

Uji tugas teman (cari rincian zona latihan 10, lalu kembali): sebelum perbaikan berhasil dengan 1 pertanyaan bantuan, skala kemudahan 4; sesudah menambah petunjuk gulir dan scrollbar, berhasil tanpa bertanya, skala 5. Waktu tidak diukur; hanya satu penguji.
