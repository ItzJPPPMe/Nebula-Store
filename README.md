# Nebula Store

**Yapımcı:** ItzJPPPMe · **Lisans:** Kapalı kaynak (özel)

Nebula Store, Steam oyunlarını açık kaynak topluluk araçları (OpenSteamTool / BetterSteamTools / Walftech) yardımıyla kütüphaneye ekleyip Steam üzerinden indirmen için tasarlanmış bir Windows masaüstü uygulamasıdır. Electron (uygulama kabuğu) + Rust (yerel arka uç) üzerine kuruludur.

> **Önemli:** Bu proje kapalı kaynaktır. Kaynak kod herkese açık değildir. Yalnızca
> yayınlanan kurulum paketi (`release/…-x64.exe`) ve sürüm akışı (`version.json`) dağıtılır.
> Herhangi birinin bu depoyu/fork'u "resmi" diye sunması durumunda lisans ihlalidir.

---

## Özellikler

- **Mağaza entegrasyonu** — Steam arama, paket (bundle), DLC ve oyun ayrıntıları.
- **Kütüphane yönetimi** — Tümü ücretsiz, indirilebilir oyunlar; kurulum, doğrulama, kaldırma.
- **Unlocker kurulumu** — OpenSteamTool (OST) / BetterSteamTools (BST) tek tıkla kurulum ve durum takibi.
- **Walftech entegrasyonu** — Manifest + licencedb + depotcache hazırlama.
- **Otomatik güncelleme** — `version.json` tabanlı sürüm bildirimi, indirme ve sessiz kurulum.
- **Çoklu tema + vurgu rengi** — Steam/Cyberpunk/Dark/Midnight ve daha fazlası.
- **Ağ tanılama** — DNS, HTTPS erişilebilirlik, saat sapması ve CDN kontrolüyle sorun ayıklama.
- **Çoklu indirme kaynağı** — Walftech (yerleşik) + kullanıcı anahtarı ile ek kaynaklar.

## Sürüm akışı (auto-update)

Uygulama başlangıçta ve "Mağaza" görünümünde sürüm akışını denetler.

- Akış dosyası: `version.json` (bu deponun kökünde) — doğrudan:
  - `https://raw.githubusercontent.com/ItzJPPPMe/nebula-store/main/version.json`
- Sürüm dosyası ŞU şemada olmalıdır:
  ```json
  {
    "name": "Nebula Store",
    "version": "1.1.0",
    "channel": "stable",
    "url": "https://example.com/nebula-store-1.1.0-x64.exe",
    "checksum": "sha256:…",
    "minVersion": "1.0.0",
    "released": "2026-10-11",
    "notes": ["Bu sürümde neler değişti"]
  }
  ```
- `url`, `Nebula Store-{version}-x64.exe` kurucusunun (NSIS) doğrudan indirme bağlantısıdır.
- Akış adresi ayarlanabilir:
  - Kullanıcı verisi klasöründe `update-feed.json` içine `{ "url": "…" }` yazarak
    (`%APPDATA%\nebula-store\update-feed.json`)

## Geliştirme

```bash
npm install
npm run build:native   # Rust N-API derlemesi
npm run dist           # native + Windows paket ("release")
npm test               # birim/E2E testleri
npm run test:steam
npm run test:all
```

Uygulamayı geliştirici modunda çalıştırmak için: `npm run dev`

## Sürümler

Geçmiş önemli sürümler `version.json` `notes` alanı ile duyurulur. Detaylı değişiklik geçmişi
kapalı kaynak politikası gereği yayınlanmaz; yalnızca kullanıcının göreceği sürüm notları açıktır.

## Yasal not

Nebula Store, açık kaynak kişisel kullanım bütünleştirmeleri üzerine kuruludur ve yalnızca
sahip olduğun/ücretsiz oyunlar ile kendi sisteminde kullanım için tasarlanmıştır. Telif hakkı
politikalarına uymak tamamen kullanıcının sorumluluğundadır.