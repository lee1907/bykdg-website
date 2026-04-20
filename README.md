# Bykdg — Geliştirici Portföy Sitesi

Indie mobil uygulama stüdyosu **Bykdg** için tek sayfalık statik site. Google Play Console'da **"Kişisel → Kuruluş"** hesap türü dönüşümü için kuruluş web sitesi doğrulama amacıyla hazırlandı.

## Dosyalar

```
bykdg-website/
├── index.html        Ana sayfa (hero + about + 5 uygulama + iletişim)
├── privacy.html      Gizlilik politikası (tüm 5 uygulamayı kapsar)
├── support.html      Destek / SSS sayfası
├── 404.html          Bulunamadı sayfası
├── favicon.svg       Site ikonu (B harfi, mor-pembe gradient)
├── robots.txt        Arama motorları için
├── sitemap.xml       Sitemap (URL'leri domain'ine göre güncelle)
└── README.md         Bu dosya
```

Tüm CSS ve JavaScript her HTML dosyasının içine gömülü — **harici dependency yok**, herhangi bir statik hosting'e tek tıkla deploy edilebilir.

## 🚀 Deployment Adım Adım

### Seçenek 1 — GitHub Pages (önerilen, ücretsiz)

**1. GitHub hesabı / repo oluştur**

Henüz yoksa [github.com](https://github.com)'da ücretsiz hesap aç. Geliştirici adın ile uyumlu bir kullanıcı adı seç (örn: `bykdg`).

**2. Repo oluştur**

- GitHub'da → "New repository"
- Repository name: **`bykdg.github.io`** (tam olarak bu isim olmalı — kullanıcı adın ile aynı + `.github.io`)
- Public seç
- "Create repository"

**3. Dosyaları yükle**

Terminal'den (bu klasörün içinde):

```bash
cd /c/Users/Lenovo/bykdg-website
git init
git add .
git commit -m "Initial commit: Bykdg developer portfolio site"
git branch -M main
git remote add origin https://github.com/BYKDG-KULLANICIADIN/bykdg.github.io.git
git push -u origin main
```

Ya da web arayüzünden: repo sayfasında "uploading an existing file" → tüm dosyaları sürükle bırak → commit.

**4. Pages'i aktif et**

- Repo → Settings → Pages
- Source: **Deploy from a branch**
- Branch: **main** / root
- Save

**5. Bekle & ziyaret et**

1-5 dakika içinde site yayında olur:
👉 `https://KULLANICIADIN.github.io`

### Seçenek 2 — Netlify (drag & drop, GitHub gerekmez)

1. [netlify.com](https://www.netlify.com) → Sign up (Google ile giriş yapabilirsin)
2. "Add new site" → "Deploy manually"
3. Bu klasörü (bykdg-website) aç → tüm dosyaları seç → sürükle bırak
4. Otomatik URL atanır (örn: `https://bykdg-xyz.netlify.app`)
5. İstersen Site settings → Domain management → custom domain ekle

### Seçenek 3 — Vercel

1. [vercel.com](https://vercel.com) → Sign up
2. Import → Upload folder → bykdg-website
3. Deploy → URL alırsın

## 🌐 Özel Alan Adı (Opsiyonel — Ama Önerilen)

Google doğrulaması için **kendi alan adın** daha profesyonel durur (`bykdg.com` gibi). Namecheap, GoDaddy veya Turkticaret'ten yıllık ~$10-15'e alabilirsin.

### GitHub Pages'e özel domain bağlama

1. Alan adını satın al (örn: `bykdg.com`)
2. Domain sağlayıcında DNS ayarları:
   - **A kayıtları** (4 adet, `@` için):
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - **CNAME kaydı** (`www` için): `BYKDG-KULLANICIADIN.github.io`
3. Repo → Settings → Pages → Custom domain → `bykdg.com` yaz → Save
4. "Enforce HTTPS" kutusunu işaretle (DNS yayıldıktan sonra)
5. Klasöre `CNAME` isimli (uzantısız) bir dosya ekle içinde sadece `bykdg.com` yazsın → commit → push

### Alan adı ile robots.txt ve sitemap.xml güncelle

Domain'ini satın alıp bağladıktan sonra:
- `robots.txt` içinde `https://bykdg.github.io/sitemap.xml` → `https://bykdg.com/sitemap.xml` yap
- `sitemap.xml` içindeki tüm `bykdg.github.io` → `bykdg.com` ile değiştir

## ✅ Google Play Console Doğrulama

Site yayında olduktan sonra:

1. **Play Console → Settings → Developer account → Account details**
2. **Hesap türünü değiştir** butonuna bas
3. Açılan formda web sitesi URL'sini gir: `https://bykdg.github.io` (veya özel alan adın)
4. Google Search Console doğrulaması isterse:
   - [search.google.com/search-console](https://search.google.com/search-console) → Add property
   - URL prefix: siteyi gir
   - "HTML file" doğrulama yöntemini seç → Google'ın verdiği dosyayı indirip sitenin kök dizinine ekle → yeniden deploy et → Verify
   - Ya da "DNS record" yöntemi (özel domain kullanıyorsan) — TXT kaydı ekle
5. Doğrulama tamamlandıktan sonra Play Console'a geri dön, kuruluş adını **"Bykdg"** olarak gir
6. Talebi gönder — Google 1-7 gün içinde yanıt verir

## 🎨 Renk Paleti

Sitenin teması Shevana'nın ikon renklerinden esinlenildi:

| İsim | Kod | Kullanım |
|---|---|---|
| Purple | `#7C4DFF` | Birincil renk, butonlar |
| Purple Dark | `#5E35B1` | Gradient koyu taraf |
| Accent Pink | `#FF6EC7` | Vurgu, hover |
| Background | `#0F0B1F` | Sayfa arka planı |
| Card BG | `#1A1330` | Kart arka planı |

## 📝 İçerik Güncelleme

- **Yeni uygulama eklemek:** `index.html` içinde `.apps-grid` bölümüne yeni bir `<div class="app-card">` kopyala
- **İletişim e-postasını değiştirmek:** Tüm HTML dosyalarında `alibykdag@gmail.com` yerine yenisini koy
- **Logo/isim değişimi:** Her HTML'deki `.logo` class'lı elementlere dokun

## Lisans

© Bykdg — Tüm hakları saklıdır. Kaynak kodu kişisel kullanım içindir.
