# Dokumentasi & Panduan Praktikum 2 (Pemrograman Web)

Repositori ini memuat implementasi website portofolio sederhana yang memenuhi seluruh kriteria Praktikum 2 mata kuliah Pemrograman Web menggunakan standar murni **HTML5, CSS3, dan JavaScript sederhana**.

---

## 1. Struktur Layout Semantik HTML5

Mengikuti skema layout modul praktikum:
- `<header>`: Identitas halaman, subjudul, dan wadah running text.
- `<nav>`: Baris menu navigasi horizontal (sticky di bagian atas).
- Bagian Tengah (`.main-layout`):
  - `<aside>` (**Kiri**): Berisi menu navigasi samping, daftar keahlian teknis, dan informasi kontak cepat.
  - `<main>` (**Kanan**): Memuat 2 baris konten utama:
    - **Baris 1 (`<article id="profil">`)**: Ringkasan profil dan badge status.
    - **Baris 2 (`<section id="portofolio">`)**: Grid kartu proyek dengan thumbnail (`<figure>`) dan tombol detail.
- `<footer>`: Catatan hak cipta di bagian paling bawah halaman.

---

## 2. Konsep Kunci CSS (Persiapan UTS Live Coding)

### A. CSS Reset & Box Sizing
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box; /* Ukuran elemen mencakup padding & border */
}
```

### B. CSS Grid untuk Layout 2 Kolom
```css
.main-layout {
    display: grid;
    grid-template-columns: 1fr 2.5fr; /* 1 bagian aside (kiri), 2.5 bagian main (kanan) */
    gap: 24px;
}
```

### C. CSS Grid Responsif untuk Galeri Thumbnail
```css
.portfolio-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 16px;
}
```

### D. Animasi Running Text Murni CSS (`@keyframes`)
```css
.running-text-content {
    display: inline-block;
    padding-left: 100%;
    animation: running-text 18s linear infinite;
}

@keyframes running-text {
    0% { transform: translateX(0); }
    100% { transform: translateX(-100%); }
}

/* Jeda saat di-hover */
.running-text-wrapper:hover .running-text-content {
    animation-play-state: paused;
}
```

### E. Transisi Elemen (`transition`)
```css
.project-card {
    transition: transform 0.25s ease, box-shadow 0.25s ease;
}

.project-card:hover {
    transform: translateY(-4px); /* Efek melayang */
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.06);
}
```

### F. Media Queries (Responsivitas Layar)
```css
/* Layar Tablet & Mobile: Berubah menjadi 1 kolom tumpukan */
@media (max-width: 768px) {
    .main-layout {
        grid-template-columns: 1fr;
    }
    .site-main { order: 1; }
    .site-aside { order: 2; }
}

/* Layar Smartphone: Menu vertikal penuh */
@media (max-width: 480px) {
    .nav-menu {
        flex-direction: column;
    }
    .portfolio-grid {
        grid-template-columns: 1fr;
    }
}
```

---

## 3. Fitur JavaScript (`script.js`)

1. **Smooth Scroll**: Melakukan transisi pengguliran halus saat menu navigasi berbasis anchor (`#id`) diklik.
2. **Interaksi Tombol**: Event listener sederhana pada tombol kontak dan kartu proyek.

---

## 4. Cara Menjalankan Secara Lokal

1. Letakkan folder ini di dalam direktori `c:\xampp\htdocs\css-web-page\`.
2. Jalankan Apache dari XAMPP Control Panel.
3. Buka browser dan akses: `http://localhost/css-web-page/` atau cukup buka langsung file `index.html` di browser favorit Anda.
