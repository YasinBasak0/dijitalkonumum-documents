# Production Deployment Checklist

Bu checklist, site yayına alınmadan önce tamamlanması gereken zorunlu kontrolleri tanımlar.

---

# A) Build & Environment

## 1. Build Tipi

- Static Site Generation (SSG)
- SPA modu yok
- Gereksiz client-side hydration yok

## 2. Environment Ayrımı

- Production domain tanımlı
- Staging domain noindex
- Canonical production domain’e sabit

## 3. Build Çıktısı

- dist klasörü temiz
- Unused CSS purge aktif
- JS bundle minimal

---

# B) Performans Kontrolleri

## 1. Lighthouse (Mobile)

- Performance ≥ 90
- Accessibility ≥ 90
- Best Practices ≥ 90
- SEO ≥ 90

## 2. Core Web Vitals

- LCP ≤ 2.5s
- CLS ≤ 0.1
- INP ≤ 200ms

## 3. Görseller

- WebP / AVIF
- Responsive srcset
- Lazy load (hero hariç)

## 4. Font

- Self-host
- font-display: swap
- FOIT yok

---

# C) SEO Teknik Kontroller

## 1. Meta

Her sayfada:

- Unique title
- Unique description
- Canonical
- OG tags
- Twitter card

## 2. Robots

- Production: index,follow
- Staging: noindex,nofollow

## 3. Sitemap

- Otomatik üretilmiş
- Blog dahil
- robots.txt içinde referans var

---

# D) Schema Validasyonu

Her sayfa:

- Organization
- WebSite
- WebPage
- Breadcrumb

Metodoloji:

- Service

Blog post:

- BlogPosting

Test araçları:

- Google Rich Results Test
- Schema Validator

Hata yok.

Warning minimum.

---

# E) Güvenlik Kontrolleri

## HTTP Header’lar

- Content-Security-Policy
- X-Frame-Options
- X-Content-Type-Options
- Referrer-Policy

## Cloudflare

- SSL aktif
- Brotli açık
- Basic WAF açık
- Cache ayarları doğru

---

# F) Form Kontrolleri

- Honeypot çalışıyor
- Rate limit aktif
- Invalid data reject ediliyor
- Spam test edilmiş
- Submit sonrası analytics event çalışıyor

---

# G) Analytics

- CTA click event
- Form submit event
- Scroll depth event
- Blog read time event

---

# H) Son Kontrol

- 404 sayfası var
- 500 fallback var
- Favicon var
- OG image düzgün
- Mobil breakpoint’ler düzgün

---

# 🎯 Deployment Tamam Tanımı

Site:

✔ Hızlı

✔ Güvenli

✔ Schema valid

✔ Minimal

✔ Production-ready