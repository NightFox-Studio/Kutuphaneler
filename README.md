# Kutuphaneler

Vulpes'in Python/Linux ortamını (bootstrap) derleyen depo.

## Neden kendimiz derliyoruz?
Termux paketleri `/data/data/com.termux/...` yoluna göre derlenmiştir. Vulpes'in paket adı `com.nightfox.vulpes` olduğu için
paketlerin bu yola göre **yeniden derlenmesi** gerekir. Bunu GitHub Actions yapar.

## Nasıl çalıştırırım?
1. Bu depoya dosyaları yükle.
2. **Actions → Vulpes bootstrap derle → Run workflow**.
3. `extra` kutusuna istediğin paketleri virgülle yaz (varsayılan: `python,python-pip,git,openssl,curl`).
4. Derleme **birkaç saat** sürebilir (6 saatlik GitHub sınırı vardır). Bitince **Releases** bölümünde `bootstrap-N` çıkar,
   içindeki `bootstrap-aarch64.zip` Vulpes'in indireceği dosyadır.

## Paket nasıl eklenir?
Workflow'u yeniden çalıştırırken `extra` kutusuna adı ekle (ör. `python,python-pip,git,openssl,curl,ffmpeg`).
Paket adları Termux paket adlarıdır (termux-packages deposundaki klasör adları).

## Önemli notlar
- "Her kütüphaneyi" koymak mümkün değil. Bootstrap'a temel araçlar girer. Saf Python kütüphaneleri (telethon, requests…)
  `pip` ile PyPI'dan iner. Derleme gerektirenler (aiohttp, cryptography, numpy…) için ayrıca paket eklemek gerekir.
- Bu workflow **deneysel**: termux-packages sürekli değişir, ilk çalıştırmada hata çıkabilir. Hata olursa
  `bootstrap-ve-log` çıktısındaki `build.log` dosyasının son satırlarını gönder, birlikte düzeltiriz.
- Paketlerin kendi lisansları vardır (python: PSF, git: GPLv2, openssl: Apache-2.0…). Dağıtırken lisans bildirimini koru.
- Termux ile bağlantılı bir proje değildir.
