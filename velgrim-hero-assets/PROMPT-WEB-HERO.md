# PROMPT MASTER: VELGRIM / CRIMSON BLAZE HERO

Bertindak sebagai senior frontend engineer, creative developer, dan art director untuk website game AAA. Bangun halaman website yang BENAR-BENAR BERFUNGSI dengan tampilan hero yang semirip mungkin dengan gambar `reference-hero.png`. Jangan hanya membuat mockup, screenshot, Canva, atau satu gambar fullscreen. Gunakan seluruh asset PNG terpisah yang disediakan. Fokus utamanya adalah komposisi visual yang sangat presisi, layer compositing, interaksi yang nyata, animasi parallax mouse dan scroll yang halus, serta performa yang terjaga.

## Teknologi
- React + TypeScript + Vite + Tailwind CSS.
- Motion for React (`motion/react`) untuk animasi dan spring/parallax, atau GSAP + ScrollTrigger apabila perlu pin/scroll yang lebih kompleks. Jangan gunakan keduanya sekaligus untuk animasi yang sama.
- Gunakan CSS custom untuk positioning pixel-accurate dan efek visual; lucide-react untuk ikon interaktif.
- Tuliskan kode runnable lengkap: package.json, components, hooks, CSS, konfigurasi font, dan instruksi run.

## Asset dan penggunaan
Semua aset ada di `public/assets/`:
- `reference-hero.png`: screenshot TARGET VISUAL. Hanya untuk referensi visual, JANGAN ditampilkan sebagai background final.
- `background.png`: background crimson dengan swirl, isi seluruh hero pakai `background-size: cover; background-position: center`.
- `title-crimson-blaze.png`: headline raksasa putih distressed bertuliskan CRIMSON BLAZE, di belakang karakter.
- `character.png`: PNG transparan gadis anime rambut gelap dengan telinga elf, mata amber dan pedang api; jadi foreground utama.
- `particles-overlay.png`: overlay bara, asap, serpihan kelopak merah, dan light trails; letakkan di atas karakter sebagian dan gunakan pointer-events:none.
- `logo-velgrim.png`: logo VELGRIM bawah tengah.
- `navbar-overlay.png`: acuan tampilan navbar, tetapi navigasinya HARUS dibangun sebagai teks dan tombol HTML supaya bisa diklik, diakses keyboard, dan responsif.
- `button-begin-journey.png`: acuan skin tombol CTA merah; boleh dijadikan image background/dekorasi di dalam button HTML, tetapi tetap gunakan elemen `<button>` atau `<a>`.
- `button-watch-trailer.png`: acuan skin tombol trailer gelap; tetap harus interaktif.
- `social-icons.png`: acuan visual ikon sosial; buat masing-masing icon sebagai `<a>` terpisah (SVG/lucide/ikon platform).
- `tagline.png`: acuan kalimat kiri bawah; utamakan actual text HTML untuk ketajaman dan aksesibilitas.

## Komposisi desktop 1672 × 941 (rasio sekitar 16:9)
- Hero setinggi minimal `100svh`, `position:relative`, `overflow:hidden`, dominan crimson/black. Hindari ruang putih, kartu dashboard, panel rounded generik, gradient ungu/biru, atau desain template startup.
- Background `background.png` paling belakang; tambahkan vignette transparan gelap di pinggir dan sedikit glow merah di tengah. Pertahankan swirl ornamental.
- Navbar di atas pada sekitar y=24–55 px dari tepi atas: logo putih star + `VELGRIM` kiri dengan margin sekitar 4–5%; menu `HOME`, `WORLD`, `CHARACTERS`, `MEDIA`, `NEWS` di bagian atas tengah, huruf putih uppercase tracking lebar; HOME punya underline merah menyala. Search icon dan tombol outline chamfered `PLAY NOW` di kanan. Navbar di atas semua image hero dan tidak tertutup karakter.
- Di y sekitar 110 px tampilkan eyebrow `A S H E S   A W A K E N` dengan huruf serif putih dan tracking besar, di atas headline.
- Headline `CRIMSON BLAZE` putih/cream ultra-bold condensed, sangat besar, lebar kurang lebih 88% viewport, dari area y sekitar 135 px sampai ~610 px. Gunakan `title-crimson-blaze.png`, bukan judul kecil biasa. Text harus di BELAKANG karakter, jangan sembunyikan seluruhnya. Jika image title sulit menyesuaikan, boleh gunakan font `Anton` / `Bebas Neue` plus tekstur distressed sebagai fallback. Tambahkan heading semantik untuk aksesibilitas.
- Karakter mendominasi area tengah-kanan (focal point kira-kira x=57%, y=52%). Skalakan `character.png` agar wajah ada di sekitar sepertiga atas, dan pedang menyilang diagonal dari kanan-atas ke kiri-bawah. Ilustrasi boleh melewati batas layar pada bawah dan kanan (intended cropping) seperti referensi; jangan stretch rasio aspect gambar. Karakter di DEPAN tulisan. Tambahkan glow oranye sangat halus di area pedang, bukan blur pada wajah/karakter.
- Teks kecil kiri bawah, kira-kira x=5%, y=66%: `A WORLD REBORN` / `THROUGH FIRE AND WILL.` dengan serif putih dan letter-spacing besar.
- Tepat di bawah teks (sekitar y=75–82%): dua CTA horizontal: tombol merah chamfered `BEGIN YOUR JOURNEY` + panah, dan tombol dark outline `WATCH TRAILER` + ikon play. Gaya tipis cinematic game UI, bukan rounded pill modern generik.
- Bawah kiri (sekitar y=91–94%): indikator slide `01` dan garis horizontal tipis.
- Bawah tengah (sekitar y=85–96%): emblem dan logo `VELGRIM` + subheading `ECHOES OF THE SCARLET SKY`. Gunakan image logo jika cocok.
- Bawah kanan (sekitar y=91–94%): garis pemisah + ikon Discord, YouTube, X, Instagram putih kecil, masing-masing clickable dengan label aksesibilitas.
- Tumpuk beberapa lapisan pada z-index berurutan: backdrop 0, vignette 1, title 2, background sparks 3, character 4, foreground particles 5, left CTA/captions 7, logo/footer 8, navbar 10. Bila overlay menutupi tombol, perbaiki pointer events dan z-index.
- Targetkan hasil pertama yang sedekat mungkin dengan `reference-hero.png`; buat komposisi dulu sebelum menambahkan animasi.

## ANIMASI DAN INTERAKSI PREMIUM
1. **Mouse parallax cinematic**: track mouse di area hero, normalisasi x/y -1 s.d. 1, gunakan spring yang lembut. Background bergerak sekitar 4–8 px berlawanan arah mouse; headline 10–14 px; character 18–24 px; foreground embers 26–36 px. Jangan sampai layer tampak lepas posisi atau ada gap. Pada touch device matikan mouse-parallax.
2. **Scroll parallax**: ketika scroll halaman, background translasi perlahan (+~50 px), headline bergeser naik ~90 px dan opacity sedikit turun, karakter bergerak naik ~140 px / scale 1.02, partikel naik ~200 px. Gunakan transforms, clamp dan easing, bukan perubahan top/left terus menerus. Tambahkan section lanjutan di bawah hero supaya scroll benar-benar bisa diuji.
3. **Entrance sequence** setelah load: vignette/background fade 0–600 ms; headline reveal dari bawah dengan opacity dan clip-path 250–1250 ms; karakter muncul dari bawah + scale 1.045 menuju 1 dengan glow lembut dalam 1.4 s; eyebrow dan tagline fade stagger; tombol masuk dengan subtle upward reveal; navbar fade; logo bottom muncul belakangan. Hindari animasi berlebihan sampai menggeser layout.
4. **Ember particle system**: gunakan Canvas 2D atau DOM particles ringan (sekitar 35–60 particles desktop, lebih sedikit mobile), dengan ukuran dan opacity acak, gerakan perlahan naik serta sedikit menyamping, warm glow orange/red, loop berkelanjutan. Jaga frame rate 60 fps jika perangkat mendukung; berhenti saat tab tidak terlihat. `particles-overlay.png` tetap menjadi efek statis dekoratif di belakang particle animasi.
5. **Fire glow**: glow oranye di sekitar sword dengan CSS pseudo-element/blur yang berdenyut sangat halus (opacity 0.65–0.9); sedikit sparks dekat pedang, tapi jangan memalsukan bentuk sword tambahan.
6. **Microinteractions**: underline menu bergeser halus mengikuti active/hover; `PLAY NOW` border glow on hover; tombol CTA ada subtle light sweep dari kiri ke kanan dan naik 2 px saat hover; tombol WATCH TRAILER memutar ikon play sedikit saat hover; optional custom warm cursor glow di desktop (`pointer-events:none`).
7. **Klik benar-benar berfungsi**: `BEGIN YOUR JOURNEY` scroll smooth ke section `#world` di bawah hero. `WATCH TRAILER` membuka modal responsive dengan tombol close/Escape; jika URL video belum tersedia tampilkan state `Trailer belum tersedia`, jangan embed URL palsu. Menu nav mengarah ke anchor konten sederhana yang memang ada. PLAY NOW bisa mengarah ke section #world sementara dengan label yang jelas atau diatur lewat config. Semua sosial memakai URL configurable, jangan gunakan `href="#"` yang menipu.
8. **Reduced motion**: hormati `prefers-reduced-motion`, disable parallax berlebih dan particles, tampilkan komposisi statis yang tetap indah. Berikan fallback pada Safari/mobile.

## Responsif
- Desktop 1440–1920 px: komposisi setia seperti screenshot acuan.
- Tablet 768–1023 px: perkecil headline, pindahkan karakter sedikit ke kanan, CTA tetap terbaca dan tidak bertabrakan.
- Mobile 360–767 px: navbar ringkas (logo kiri, hamburger menu kanan, menu drawer yang bisa dibuka/tutup), karakter di tengah atau center-right dengan crop artistik, headline dibelakang karakter, tagline/CTA diletakkan pada zona yang tetap terbaca dengan gradient overlay; footer minimal; jangan sampai horizontal scrolling atau tulisan terpotong buruk.
- Gunakan `clamp()`, `svh`, `aspect-ratio`, `object-fit:contain`, dan breakpoint CSS yang nyata, jangan hanya shrink seluruh desktop.

## Kualitas dan batasan
- Jangan gunakan `reference-hero.png` sebagai satu gambar fullscreen palsu.
- Jangan satukan semua image menjadi 1 background; setiap layer benar-benar terpisah agar bisa parallax.
- Jangan gunakan `character.png` sebagai CSS background untuk seluruh viewport; gunakan `<img>` absolut dengan preserved aspect ratio dan positioning yang terkontrol.
- Semua navbar/menu/CTA harus merupakan elemen HTML yang berfungsi, bukan gambar dekoratif yang tidak bisa diklik.
- Jangan gunakan animasi yang membuat tampilan blur, janky, atau menghalangi pembacaan teks.
- Optimalkan ukuran image, pertahankan transparansi untuk layer yang memang transparan, siapkan preload hero assets utama, serta hindari layout shift. `will-change:transform` hanya pada layer yang bergerak.
- Pakai CSS variables untuk layer offsets, kecepatan parallax dan warna agar mudah disetel.
- Buat struktur komponen misalnya `Hero`, `Navbar`, `HeroTitle`, `HeroCharacter`, `ParticleField`, `HeroCTA`, `HeroFooter`, `TrailerModal`, `usePointerParallax`.

## Deliverables dan verifikasi
1. Kode proyek lengkap yang dapat dijalankan lokal tanpa error.
2. Struktur file yang jelas, seluruh assets dipakai dengan path yang benar.
3. Perbandingan visual pada viewport 1672×941: background, posisi wajah, diagonal pedang, headline, CTA, navbar dan footer mengikuti target screenshot sedekat mungkin. Koreksi CSS positioning bila meleset.
4. Interaksi tombol/modal/menu bekerja, animasi mouse/scroll terlihat jelas tetapi elegan, dan reduced-motion tidak rusak.
5. Tampilkan preview desktop dan mobile. Hasil harus terasa sebagai landing page anime fantasy AAA yang premium, bukan template biasa.

PENTING: Prioritaskan **kesamaan visual dengan `reference-hero.png`** di atas kebebasan mendesain ulang. Buat hero seakurat mungkin dari layer yang tersedia. Setelah visual cocok, baru implementasikan motion yang halus tanpa mengubah posisi resting layout.
