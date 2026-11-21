# -Otonoha-pemutar-musik
音の葉 Otonoha: pemutar musik web bergaya Jepang dalam satu file HTML. Seret &amp; lepas banyak file atau folder, tag, cover, dan lirik terbaca otomatis. Tanpa server.

<div align="center">

# 音の葉 Otonoha

**Pemutar musik web bergaya Jepang. Satu file HTML, tanpa server, tanpa instalasi.**

*"Daun-daun suara", putar koleksi musikmu langsung dari browser.*

![Satu file](https://img.shields.io/badge/satu%20file-HTML-c4506b)
![Tanpa dependensi](https://img.shields.io/badge/dependensi-0-7f9f73)
![Lisensi MIT](https://img.shields.io/badge/lisensi-MIT-2d3250)

![Tampilan Otonoha](docs/screenshot.png)

</div>

## Tentang

Otonoha adalah pemutar musik yang berjalan sepenuhnya di browser. Seret file musik atau satu folder penuh ke jendela, dan judul, artis, cover, serta lirik terisi otomatis dari tag file. Semua data tersimpan di perangkatmu sendiri, tidak ada yang dikirim ke server.

## Fitur

**Impor**
- Seret & lepas banyak file sekaligus, atau seluruh folder (tombol **⬆ Impor** dan **📁 Folder** juga tersedia).
- Judul, artis, genre, cover, dan lirik dibaca otomatis dari tag **ID3 (MP3), M4A/MP4, FLAC, OGG Vorbis, dan Opus**.
- Tanpa tag? Judul dan artis ditebak dari nama file, misalnya `01 - Artis - Judul.mp3`.
- Nama folder otomatis menjadi **Koleksi** (atau nama album jika file diseret tanpa folder).
- File `.lrc` dengan nama sama otomatis dipasangkan sebagai lirik.
- **File video klip** (`.mp4`, `.webm`, `.mkv`, dll.) diputar sebagai audio, dengan thumbnail dari satu frame videonya.
- Lagu yang sudah pernah diimpor tidak ditambahkan dua kali.
- Lagu juga bisa ditambahkan lewat tautan audio (`https://…` atau `file:///…`).

**Pustaka**
- Koleksi, playlist (urutan bisa diatur), tag, rating bintang, dan favorit.
- Pencarian, pengurutan, dan paginasi.
- Aksi massal: pilih banyak lagu lalu pindahkan koleksi, tambah ke playlist, beri tag, atau hapus.
- Backup dan restore seluruh data ke file JSON.

**Pemutaran**
- Acak, ulangi (semua / satu / mati), seek, dan volume.
- **Mode fokus** dengan piringan hitam berputar dan lirik tersinkron (format LRC). Klik baris lirik untuk melompat.
- Kontrol media dari keyboard dan sistem (Media Session API).
- Tema terang dan gelap.
- Tanpa lagu? Ada **nada koto sintetis** untuk demo.

## Cara memakai

**Langsung dari browser**
1. Unduh `index.html`.
2. Buka dengan Chrome, Edge, Firefox, atau Safari.
3. Seret musikmu ke jendela.

**Lewat GitHub Pages**
1. Buka *Settings → Pages* di repo ini.
2. Pilih branch `main` dan folder `/ (root)`.
3. Buka `https://USERNAME.github.io/otonoha/`.

## Pintasan keyboard

| Tombol | Fungsi |
|---|---|
| `Spasi` | Putar / jeda |
| `←` `→` | Mundur / maju 5 detik |
| `F` | Buka / tutup mode fokus |
| `L` | Tampilkan / sembunyikan lirik |
| `M` | Bisukan |
| `Shift` + `↑` `↓` | Volume (di mode fokus) |
| `Esc` | Tutup mode fokus atau dialog |

## Penyimpanan data

| Data | Disimpan di |
|---|---|
| Daftar lagu, koleksi, playlist, tag, rating | `localStorage` browser |
| File audio hasil impor | `IndexedDB` browser, jadi tetap bisa diputar setelah halaman dimuat ulang |
| Cover | Thumbnail kecil di `localStorage` |

Catatan:
- Browser tidak mengizinkan halaman web membaca jalur lengkap file (seperti `C:\Musik\…`), jadi Otonoha menyimpan salinan file di browser, bukan jalurnya.
- File audio memakai ruang disk browser. Menghapus lagu dari pustaka juga menghapus salinannya.
- Data terikat pada browser dan alamat halaman. Pakai **Backup** untuk memindahkan daftar lagu ke tempat lain. Backup hanya berisi daftar dan metadata, bukan file audionya.

## Format & kompatibilitas

- **Tag dibaca:** MP3 (ID3v1/v2), M4A/MP4/MOV, FLAC, OGG, Opus.
- **Bisa diputar:** apa pun yang didukung browsermu. MP3, AAC, FLAC, OGG, dan WAV aman di browser modern. Video MKV atau codec yang tidak umum bisa gagal diputar.
- Tag berencoding lama (misalnya Shift-JIS) bisa tampil acak. Tag Unicode aman.
- Font memakai Google Fonts (Shippori Mincho dan Zen Maru Gothic). Tanpa internet, tampilan memakai font cadangan sistem.

## Struktur repo

```
otonoha/
├── index.html        # seluruh aplikasi (HTML + CSS + JS)
├── docs/
│   └── screenshot.png
├── README.md
├── LICENSE
└── .gitignore
```

## Pengembangan

Tidak ada proses build. Edit `index.html`, lalu muat ulang browser. Untuk menjalankannya lewat server lokal:

```bash
python3 -m http.server 8000
# buka http://localhost:8000
```

## Kontribusi

Saran dan perbaikan dipersilakan. Buka *issue* untuk melaporkan bug atau mengusulkan fitur, atau kirim *pull request* langsung.

## Lisensi

[MIT](LICENSE)
