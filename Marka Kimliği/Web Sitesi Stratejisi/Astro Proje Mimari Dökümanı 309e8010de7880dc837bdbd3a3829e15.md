# Astro Proje Mimari Dökümanı

Bu doküman, DijitalKonumum web sitesinin:

- Schema-first
- Semantic
- Minimal
- Yüksek performanslı
- Üretime hazır

şekilde inşa edilmesi için teknik mimariyi tanımlar.

---

# 0️⃣ Kurulum Stratejisi

Proje:

- Astro tabanlı
- Static Site Generation (SSG)
- Tailwind CSS ile tasarım
- MDX ile içerik yönetimi

Build tipi:

- Tam statik export
- Client-side JS minimum
- SPA değil

Amaç:

- Maksimum hız
- Minimum JS
- AI + arama motorları için net okunabilir yapı

---

# 1️⃣ Proje Klasör Organizasyonu

Proje modüler ve sorumluluklara ayrılmıştır:

### `layouts/`

Ortak layout yapısı.

- SEO burada merkezi yönetilir.
- Schema burada merkezi enjekte edilir.
- Header/Footer globaldir.

Amaç:

Her sayfada tekrar kod yazmamak.

---

### `components/`

Tekrarlanan UI ve sistem bileşenleri.

- SEO component
- Schema component
- Header
- Footer
- CTA

Amaç:

Tutarlılık ve kontrol.

---

### `content/`

Blog içerikleri.

- MDX tabanlı
- Frontmatter zorunlu
- Schema üretimi bu metadata’dan beslenir

Amaç:

İçerik ve sunum ayrımı.

---

### `pages/`

Statik route’lar.

- Ana sayfa
- Metodoloji
- Neden
- Hakkımızda
- İletişim
- Blog index
- Blog dinamik slug

Amaç:

Net URL yapısı ve statik üretim.

---

### `lib/`

Merkezi konfigürasyon ve schema üretim mantığı.

- Site bilgileri
- Schema generator fonksiyonları

Amaç:

Hardcoded dağınıklığı engellemek.

---

### `public/`

Statik dosyalar.

- robots.txt
- görseller
- ileride fontlar

---

# 2️⃣ Merkezi Site Konfigürasyonu

Tüm site meta bilgileri tek bir yerde tutulur:

- Site adı
- Domain
- Canonical base
- Locale
- Email
- AreaServed

Amaç:

✔ Tek kaynaklı doğruluk

✔ Tutarlılık

✔ Schema ve SEO’da hata önleme

---

# 3️⃣ Tasarım Sistemi (Tailwind Yapılandırması)

Tasarım:

- Minimal
- 2 ana renk
- Sabit spacing scale
- Harf aralığı kontrolü
- Max content width sabit

Theme genişletmeleri:

- Marka renkleri
- Logo letter spacing
- Content max width

Amaç:

✔ Tasarımın dağılmaması

✔ Her sayfanın aynı dili konuşması

✔ Premium minimal çizgi

---

# 4️⃣ SEO Mimarisi

Her sayfa:

- Title
- Description
- Canonical
- OG
- Twitter card
- Robots directive

zorunlu içerir.

SEO component merkezi çalışır.

Amaç:

✔ Meta tekrarını engellemek

✔ Tutarlı OpenGraph üretmek

✔ Staging/production ayrımı yapmak

---

# 5️⃣ Schema Mimarisi

Schema yaklaşımı:

“Schema-first”

Yani:

Sayfa tasarımından bağımsız olarak anlam yapısı en başta düşünülür.

---

## Merkezi Schema Türleri

Her sayfada:

- Organization
- WebSite
- WebPage
- BreadcrumbList

Metodoloji sayfasında ek:

- Service (DGK)

Blog yazılarında ek:

- BlogPosting
- Article

Amaç:

✔ AI okunabilirlik

✔ Anlam netliği

✔ Tutarlılık

---

# 6️⃣ Base Layout Stratejisi

Base layout:

- SEO component çağırır
- Schema component çağırır
- Global header/footer içerir
- Main alanı slot olarak verir

Amaç:

✔ Tek yerden kontrol

✔ Sayfa bazlı schema ekleyebilme

✔ Temiz hiyerarşi

---

# 7️⃣ Header & Footer Yapısı

Header:

- Logo (tracking ayarlı)
- Minimal navigation
- 4 linkten fazla değil

Footer:

- Minimal copyright
- Email
- Fazla link yok

Amaç:

✔ Ajans hissi vermemek

✔ Minimal kalmak

---

# 8️⃣ Ana Sayfa Mimarisi

Ana sayfa:

- Full screen hero
- Kavram alanı
- Problem teşhisi
- DGK program blok
- Kapanış CTA

Tasarım prensibi:

- Büyük tipografi
- Az ikon
- Çok boşluk
- Net hiyerarşi

---

# 9️⃣ MDX İçerik Sistemi

Blog içerikleri:

- MDX
- Frontmatter zorunlu
- title
- description
- publishDate
- tags
- canonical

Amaç:

✔ İçerik üretimini koddan ayırmak

✔ BlogPosting schema’yı metadata’dan üretmek

---

# 🔟 Robots ve Sitemap

Robots:

- Production: index
- Staging: noindex

Sitemap:

- Otomatik üretilir
- Blog içeriklerini içerir

Amaç:

✔ Crawl kontrolü

✔ Yapı doğruluğu

---

# 1️⃣1️⃣ Sayfa Bazlı Schema Yerleşim Stratejisi

Her sayfada:

Organization + WebSite + WebPage + Breadcrumb

Metodoloji sayfası:

- Service schema

Blog post:

- BlogPosting schema

Amaç:

✔ Anlamı sayfa bazında güçlendirmek

✔ Fazla schema spam yapmamak

---

# 🎯 Genel Mimarinin Stratejik Gücü

Bu yapı şunları garanti eder:

✔ Performans

✔ Minimal JS

✔ Semantic HTML

✔ Schema-first yapı

✔ Blog genişlemeye hazır

✔ Production deploy’a hazır

✔ SEO teknik uyumlu

✔ AI okunabilir