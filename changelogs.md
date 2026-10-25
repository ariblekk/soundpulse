# Changelog

Semua perubahan dan riwayat pembaruan penting pada proyek **SoundPulse** didokumentasikan di berkas ini.

Format berkas mengikuti prinsip [Keep a Changelog](https://keepachangelog.com/id/1.0.0/) dan mematuhi aturan [Semantic Versioning](https://semver.org/lang/id/).

---

## [1.0.2] - 2026-10-25

### ✨ Added
- **Queue Rebuild Action**: Tombol aksi `REBUILD` di samping tombol clear pada header antrean pemutaran untuk membuat ulang antrean rekomendasi lagu secara dinamis dari lagu yang sedang diputar.
- **Clear Queue Confirmation Dialog**: Dialog konfirmasi peringatan (`AppAlertDialog`) sebelum mengosongkan antrean lagu untuk mencegah aksi hapus yang tidak disengaja.

### 🐛 Fixed & Improved
- **Queue & Audio Player Synchronization**: Mengatasi desinkronisasi `ConcatenatingAudioSource` dengan antrean saat `clearQueue()`, penghapusan lagu aktif pada `removeFromQueue()`, serta penanganan `addToQueue()` saat player belum aktif (*reported by Ridwan Saidi*).
- **Seamless Queue Item Seeking**: Mengetuk lagu di bottom sheet antrean kini langsung melompat (*seek*) ke indeks lagu tanpa menghancurkan dan memuat ulang seluruh playlist audio source dari awal.
- **Batch Refill & Shuffle Prefetch**: Pengisian ulang antrean rekomendasi radio kini menggunakan operasi batch `addAll`, dan penentuan prefetch lagu berikutnya kini mengikuti indeks pemutar saat mode shuffle aktif.

---

## [1.0.1] - 2026-10-25

### ✨ Added
- **Chart Rank Movements**: Indikator pergerakan peringkat pada Top 50 (naik `▲`, turun `▼`, tetap `➖`, dan lagu baru `NEW`) yang dikalkulasi otomatis tiap pergantian hari di database.
- **Smart "For You" Recommendation Engine**: Sistem rekomendasi mandiri berjenjang berdasarkan aktivitas riil pendengar (`recent` → `favorites` → `search` → `top chart`) tanpa terhapus saat riwayat pencarian dibersihkan.
- **Granular Search History Removal**: Fitur hapus satu per satu kata kunci pencarian pada tab Explore via tombol close pada chip riwayat.
- **Persistent Song Credits Caching**: Penyimpanan lokal untuk song credits di memori & penyimpanan perangkat, menghilangkan kebutuhan scraping berulang kali.
- **Dynamic Home Quotes**: Koleksi teks jenaka dan jokes musik acak pada halaman Home yang otomatis berganti saat ditarik (*pull-to-refresh*).
- **In-App Update Checker & About Dialog**: Pengecekan otomatis rilis terbaru via GitHub Releases API serta peluncuran browser eksternal via native Android Intent.
- **In-App Contributors Viewer**: Integrasi tampilan kontributor komunitas langsung dari berkas markdown GitHub via native Material widget.
- **Persistent Playback State Recovery**: Pemulihan antrean lagu (*queue*), lagu terakhir, dan detik posisi pemutaran saat aplikasi dibuka kembali.

### 🐛 Fixed & Improved
- **Guest Mode Authentication**: Refactoring middleware otentikasi server agar mode tamu dapat mencari katalog lagu, melihat tangga lagu, dan streaming audio tanpa hambatan HTTP 401 (*reported by Romy Jatmiko*).
- **Task Removal Lifecycle**: Terminasi pemutar audio, notifikasi media, dan Android Foreground Service seketika aplikasi ditutup dari Recent Apps (*suggested by Ridwan Saidi*).
- **Daily Midnight Chart Cache**: Kebijakan refresh cache Top 50 di database PostgreSQL diubah menjadi harian tepat pukul 00:00 waktu server dengan proteksi fallback data lokal.
- **Optimized Home History**: Rail riwayat putar (*Recently played*) di halaman Home dibatasi 10 lagu terbaru untuk performa render yang lebih ringan dan konsisten dengan rail Top 10 Chart.

---

## [1.0.0] - 2026-10-25

### 🚀 Initial Release
- Integrasi katalog dan metadata musik Spotify.
- Resolusi dan streaming audio native dari YouTube Music.
- Pemutar audio latar belakang (*background audio*) dengan notifikasi kontrol media dan lockscreen.
- Fitur pencarian lagu, artis, album, dan genre.
- Pengelolaan pustaka musik pribadi, daftar putar (*playlist*), dan lagu yang disukai (*favorites*).
- Otentikasi sesi berbasis email dan kode verifikasi (OTP).
