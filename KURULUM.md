# ALTAY GSM — Siteyi Yayınlama

## Adım 1: Netlify'a Deploy (2 dakika)

1. **https://app.netlify.com** adresine gidin
2. Netlify hesabı yoksa ücretsiz oluşturun
3. Sayfada **"Sites"** → **"Add new site"** → **"Deploy manually"**
4. `altay-gsm` klasöründeki **tüm dosyaları** (veya tüm klasörü) sürükleyip bırakın
5. Deploy tamamlanınca size `xyz.netlify.app` gibi bir adres verilecek

## Adım 2: Domain Bağlama

1. Netlify'da sitenize tıklayın → **Domain settings** → **Add custom domain**
2. `altaygsm.com.tr` yazın
3. Netlify size **DNS kayıtlarını** gösterecek. Genelde:
   - **A Record:** `75.2.60.5` (Netlify Load Balancer)
   - **CNAME (www):** `xyz.netlify.app` (sizin Netlify adresiniz)

## Adım 3: DNS Ayarları (Domain sağlayıcınızda)

Domain'i nereden aldıysanız (nic.tr, Natro, GoDaddy vb.) oraya gidin:

| Tip   | İsim | Değer        | TTL  |
|-------|------|--------------|------|
| A     | @    | 75.2.60.5    | 3600 |
| CNAME | www  | [Netlify'daki sitenizin adresi].netlify.app | 3600 |

Örnek: Netlify siteniz `altay-gsm-abc123.netlify.app` ise:
- `www` → CNAME → `altay-gsm-abc123.netlify.app`

## Adım 4: SSL

Netlify domain bağlandıktan sonra otomatik HTTPS ekler. 24 saat içinde aktif olur.

---

**Özet:** Netlify Drop ile dosyaları yükleyin → Custom domain ekleyin → DNS'i güncelleyin.
