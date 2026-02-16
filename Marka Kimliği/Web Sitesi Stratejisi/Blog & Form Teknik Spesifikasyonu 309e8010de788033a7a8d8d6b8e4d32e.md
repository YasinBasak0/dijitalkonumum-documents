# Blog & Form Teknik Spesifikasyonu

Bu doküman, mevcut Astro + Tailwind + MDX mimarisine ek olarak:

1. Blog sisteminin üretime hazır kurulumu
2. BlogPosting schema entegrasyonu
3. Spam korumalı minimal iletişim endpoint’i

standartlarını tanımlar.

---

# 1️⃣ Blog Mimarisi

## Amaç

Blog:

- SEO için trafik aracı değildir.
- “Dijital Konum” kavramını sahiplenme aracıdır.
- DGK metodolojisine bağlanan içerik üretim alanıdır.

Her blog yazısı:

- Metodoloji sayfasına stratejik link verir.
- Tek ana konuya odaklanır.
- Uzun ama net olur.
- Gereksiz kategori karmaşası içermez.

---

## URL Yapısı

### Blog index

```
/blog
```

### Blog post

```
/blog/[slug]
```

Slug:

- Türkçe karakterler normalize edilir
- Tireli format
- Kısa
- Yıl eklenmez (zamansızlık için)

Örnek:

```
/blog/dijital-konum-nedir
```

---

## Blog Index Sayfası

### İçerik Mantığı

- Minimal grid
- Başlık + kısa açıklama
- Yayın tarihi
- Tag gösterimi opsiyonel

### Teknik Gereksinimler

- MDX content collection kullanımı
- Statik build
- Her yazıya canonical

---

# 2️⃣ BlogPosting Schema Entegrasyonu

Blog sayfalarında zorunlu:

- BlogPosting schema
- BreadcrumbList schema
- WebPage schema
- Organization schema

---

## BlogPosting JSON-LD Standardı

Her blog yazısında aşağıdaki alanlar zorunlu:

- @type: BlogPosting
- headline
- description
- datePublished
- dateModified
- author
- publisher
- mainEntityOfPage
- image (opsiyonel ama önerilir)

---

## Örnek BlogPosting Schema

```json
{"@context":"https://schema.org","@type":"BlogPosting","headline":"Dijital Konum Nedir?","description":"Görünürlük ile konum arasındaki fark ve dijital güven mimarisi.","datePublished":"2026-02-17","dateModified":"2026-02-17","author":{"@type":"Organization","name":"DijitalKonumum"},"publisher":{"@type":"Organization","name":"DijitalKonumum","logo":{"@type":"ImageObject","url":"https://www.dijitalkonumum.com/images/logo.png"}},"mainEntityOfPage":{"@type":"WebPage","@id":"https://www.dijitalkonumum.com/blog/dijital-konum-nedir"}}
```

---

## Entegrasyon Kuralı

Blog template:

- Schema, layout seviyesinde değil
- Post seviyesinde generate edilir
- Slug dinamik olarak schema içine yazılır

Zorunlu validasyon:

- Google Rich Results Test
- Schema.org validator

---

# 3️⃣ Blog İçerik Standartları

Her blog yazısı:

- Tek H1
- 3–6 H2
- Madde listeleri sınırlı
- Gereksiz keyword stuffing yok
- DGK metodolojisine doğal geçiş

Her blog yazısında:

- 1 adet metodoloji sayfası linki
- 1 adet iletişim CTA

---

# 4️⃣ İletişim Formu – Minimal Endpoint Mimarisi

## Amaç

- Premium deneyim
- Spam koruma
- Minimal veri
- Hızlı işlem

ReCAPTCHA agresif kullanılmaz.

Invisible sistem tercih edilir.

---

## Mimari Seçenekler

### Seçenek A – Serverless (Önerilen)

- Astro endpoint
- Vercel/Netlify function
- JSON body validation
- Rate limit
- Honeypot

### Seçenek B – Basit Node endpoint

- Express minimal route
- Rate limit middleware
- Email forward

---

## Zorunlu Spam Koruma Katmanları

1️⃣ Honeypot field (görünmez input)

2️⃣ IP rate limit

3️⃣ Minimum submission delay kontrolü (bot filtre)

4️⃣ Backend validation

---

## Form Alanları

Zorunlu:

- ad
- isletme
- il_ilce
- telefon

Opsiyonel:

- not

---

## Backend Validasyon Kuralları

- Telefon regex kontrolü
- Alan uzunluk limiti
- HTML injection temizliği
- Max payload limiti

---

## Başarılı Submit Sonrası

- Teşekkür ekranı
- Süreç açıklaması
- Analytics event

---

# 5️⃣ Analytics Entegrasyonu

Event’ler:

- CTA click
- Form submit success
- Scroll depth
- Blog read (time > 30s)

Tool:

- Plausible (önerilir)
- Alternatif GA4

---

# 6️⃣ Production Kuralları

Blog ve form yayına çıkmadan:

- Lighthouse ≥ 90
- CLS ≤ 0.1
- Schema valid
- Sitemap blog içeriyor
- robots.txt doğru
- Form endpoint rate limit test edilmiş

---

# 7️⃣ Stratejik Uyum

Bu sistem şunları sağlar:

✔ Kavram sahiplenme

✔ AI okunabilirlik

✔ Semantik tutarlılık

✔ Performans

✔ Güvenli form toplama

---

Bu döküman artık:

- Sadece strateji değil
- Sadece şablon değil
- Production uygulanabilir teknik spesifikasyon