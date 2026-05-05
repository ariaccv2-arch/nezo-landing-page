# NEZO Static Landing Page Plan

## Objective

Membangun landing page static untuk brand parfum NEZO yang:

- Clean, luxury, dan premium
- Fokus konversi ke Shopee
- Ringan, cepat, dan SEO-friendly
- Mudah dipindahkan ke Laravel/Blade di fase berikutnya
- Siap menjadi fondasi awal jika nanti dikembangkan menjadi e-commerce sendiri

Landing page ini bukan e-commerce penuh pada fase sekarang. Semua proses transaksi tetap diarahkan ke Shopee.

---

## Current Scope

### Phase 1: Static Landing Page

Fokus utama:

- Satu halaman landing page di `index.html`
- Produk ditampilkan langsung di halaman
- Setiap produk memiliki CTA langsung ke Shopee
- Tidak menggunakan database
- Tidak menggunakan admin panel
- Tidak ada cart, checkout, login, atau payment gateway

Tujuan fase ini adalah membuat halaman siap publish, siap iklan, dan siap menghasilkan traffic/conversion.

---

## Future Direction

Walaupun saat ini static, struktur konten tetap disiapkan agar mudah dikembangkan ke:

- Laravel + Blade
- Database produk
- Admin panel
- Checkout internal
- Payment gateway
- Order management
- E-commerce mandiri

Prinsipnya: launch cepat sekarang, scale rapi nanti.

---

## Recommended Static Structure

```text
nezo-landing-page/
|-- index.html
|-- plan.md
|-- img/
|   |-- fresh-pulse.jpeg
|   |-- ocean-breeze.jpeg
|   |-- rose-elixir.jpeg
|   |-- scandal.jpeg
|   |-- nightfall.jpeg
|   |-- royal-oud.jpeg
|   `-- aurum-luxe.jpeg
|-- favicon.ico
|-- robots.txt
`-- sitemap.xml
```

Optional jika file mulai besar:

```text
assets/
|-- css/
|   `-- style.css
`-- js/
    `-- app.js
```

Untuk fase sekarang, inline CSS/JS di `index.html` masih boleh selama mudah dirawat dan performanya aman.

---

## Content Data Model

Walaupun masih hardcoded di HTML, setiap produk sebaiknya mengikuti pola data ini:

- `name`
- `subtitle`
- `image`
- `scent_type`
- `top_notes`
- `middle_notes`
- `base_notes`
- `description`
- `shopee_url`
- `badge` optional, misalnya Best Seller atau New

Tujuannya agar nanti mudah dipindahkan ke `config/nezo.php`, lalu ke database.

Contoh struktur future-friendly:

```php
[
    'name' => 'Fresh Pulse',
    'subtitle' => 'Extrait de Parfum - 50ml',
    'image' => 'img/fresh-pulse.jpeg',
    'scent_type' => 'Fresh - Clean - Energetic',
    'top_notes' => ['Bergamot', 'Lemon', 'Green Apple'],
    'middle_notes' => ['Marine Accord', 'Jasmine'],
    'base_notes' => ['Musk', 'Amber', 'Cedarwood'],
    'shopee_url' => 'https://shopee.co.id/...',
]
```

---

## UI Sections

### 1. Navigation

- Logo NEZO
- Menu anchor: Koleksi, Tentang, Notes, Kontak
- CTA utama ke section produk atau Shopee

### 2. Hero Section

- Headline premium
- Subheadline singkat
- CTA utama
- Visual produk utama
- Harus langsung memberi kesan luxury di first viewport

### 3. Product Section

- Menampilkan semua varian parfum
- Card per produk
- Nama produk
- Tipe aroma
- Notes singkat
- CTA per produk ke Shopee

Wajib:

- CTA produk menggunakan link Shopee asli
- `target="_blank"`
- `rel="noopener noreferrer"`

### 4. About / Brand Story

- Cerita singkat tentang NEZO
- Positioning brand
- Penekanan pada premium fragrance dan simplicity in luxury

### 5. Notes Section

- Menjelaskan komposisi aroma utama
- Bisa menampilkan top, middle, dan base notes
- Tetap ringkas agar tidak mengganggu flow konversi

### 6. Benefits Section

- Extrait de Parfum
- Tahan lama
- Premium quality
- Elegant scent
- Unisex atau segmented sesuai produk

### 7. Testimonial Section

- Social proof
- Bisa mulai dari 1-3 testimonial statis
- Slider optional untuk fase berikutnya

### 8. Stats / Trust Section

- Jumlah koleksi
- Ukuran botol
- Estimasi ketahanan
- Konsentrasi parfum

### 9. Final CTA

- Penutup yang mendorong pembelian
- Tombol ke Shopee atau kembali ke koleksi

### 10. Footer

- Link sosial media
- Kontak
- Link produk
- Copyright

---

## Shopee Integration

Setiap produk harus memiliki link Shopee masing-masing.

Checklist:

- CTA utama hero jelas
- CTA tiap product card jelas
- CTA final jelas
- Semua link eksternal memakai `target="_blank"`
- Semua link eksternal memakai `rel="noopener noreferrer"`
- Jangan biarkan CTA penting berisi `href="#"`

Jika link Shopee belum tersedia, gunakan placeholder yang mudah dicari:

```html
href="SHOPEE_URL_FRESH_PULSE"
```

---

## SEO Setup

Minimal untuk static landing page:

- Meta title
- Meta description
- Canonical URL
- Open Graph title
- Open Graph description
- Open Graph image
- Twitter card
- Favicon
- `robots.txt`
- `sitemap.xml`

Target keyword awal:

- parfum premium lokal
- parfum extrait de parfum
- parfum tahan lama
- NEZO Parfume
- parfum luxury Indonesia

---

## Performance Optimization

Checklist:

- Kompres gambar
- Pertimbangkan konversi JPEG ke WebP
- Tambahkan `loading="lazy"` pada gambar non-hero
- Tambahkan width/height atau aspect ratio agar layout stabil
- Hindari dependency besar yang belum dibutuhkan
- Minify jika sudah masuk tahap deploy
- Pastikan mobile load cepat

Target:

- Landing page terasa cepat di mobile
- First viewport tampil tanpa delay besar
- Gambar produk tetap tajam tapi tidak terlalu berat

---

## Accessibility & UX

Checklist:

- Semua gambar produk punya alt text jelas
- Kontras teks cukup terbaca
- CTA mudah ditekan di mobile
- Custom cursor tidak mengganggu mobile
- Navigasi anchor bekerja
- Tidak ada teks yang overflow di layar kecil
- Animasi tidak mengganggu aksesibilitas

---

## Tracking

Optional untuk fase static:

- Google Analytics
- Meta Pixel
- TikTok Pixel jika akan beriklan di TikTok

Tujuan:

- Tracking traffic
- Retargeting ads
- Mengukur klik CTA Shopee
- Melihat produk mana yang paling banyak diminati

Event yang disarankan:

- `click_shopee_hero`
- `click_shopee_product`
- `click_shopee_final_cta`

---

## Static Launch Checklist

Sebelum publish:

- Semua gambar produk tampil
- Semua CTA penting sudah benar
- Semua produk punya link Shopee
- SEO basic terpasang
- Favicon tersedia
- Mobile responsive
- Tidak ada link penting yang masih `#`
- Tidak ada typo/encoding rusak
- Load cepat di mobile
- Sudah dites di Chrome mobile dan desktop

---

## Deployment Plan

### Static Hosting Options

- Shared hosting biasa
- VPS
- Netlify
- Vercel
- Cloudflare Pages

Karena masih static, deployment tidak perlu Laravel server.

### Optional

- CDN via Cloudflare
- Domain custom
- Image optimization tambahan

---

## Future Migration Plan

### Phase 2: Laravel Landing Page

- Pindahkan `index.html` ke Blade
- Pecah menjadi layout dan component
- Produk dipindahkan ke `config/nezo.php`
- CTA Shopee tetap digunakan

Struktur Laravel nanti:

```text
app/
`-- Http/
    `-- Controllers/
        `-- LandingController.php

config/
`-- nezo.php

resources/
|-- views/
|   |-- layouts/
|   |   `-- app.blade.php
|   |-- components/
|   |   |-- product-card.blade.php
|   |   |-- hero.blade.php
|   |   `-- section-title.blade.php
|   `-- pages/
|       `-- home.blade.php
|-- css/
|   `-- app.css
`-- js/
    `-- app.js

routes/
`-- web.php
```

Routing:

```php
Route::get('/', [LandingController::class, 'index']);
```

### Phase 3: Database

- Produk masuk ke MySQL
- Gambar produk bisa lebih dari satu
- Notes menjadi data terstruktur
- Testimonial bisa dikelola

Tabel awal:

- `products`
- `product_images`
- `fragrance_notes`
- `testimonials`

### Phase 4: Admin Panel

- Gunakan Filament
- CRUD produk
- CRUD testimonial
- Kelola hero/banner
- Kelola link Shopee

### Phase 5: E-Commerce Mandiri

- Cart
- Checkout
- Payment gateway
- Shipping integration
- Order management
- Customer account optional

Payment/shipping yang bisa dipertimbangkan:

- Midtrans atau Xendit
- Biteship atau RajaOngkir

---

## Conversion Strategy

Fokus utama:

- Visual produk kuat
- CTA jelas dan kontras
- Copy singkat tapi premium
- Social proof
- Benefit langsung terbaca
- Flow halaman tidak terlalu panjang
- Mobile-first karena traffic iklan kemungkinan besar dari mobile

Prioritas konversi:

1. Klik CTA Shopee produk
2. Explore koleksi
3. Trust lewat testimonial dan benefit
4. Follow/contact via sosial media

---

## Done Criteria

Landing page dianggap siap jika:

- Responsive di mobile dan desktop
- Semua produk tampil benar
- Semua produk punya CTA Shopee
- Link eksternal aman dengan `rel="noopener noreferrer"`
- SEO basic terpasang
- Gambar sudah dioptimasi
- Tidak ada broken image
- Tidak ada link penting kosong
- Load cepat
- Siap deploy sebagai static landing page
