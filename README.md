# sehapps.github.io

Sehapps geliştirici kökü: `https://sehapps.github.io/`

Bu repo **iki iş** yapar:

| Dosya | Ne işe yarar |
|---|---|
| `app-ads.txt` | Reklam envanterini satmaya yetkili satıcıları bildirir. **Asıl sebep bu.** |
| `index.html` | Kök adrese gelen ziyaretçiye 404 yerine kısa bir geliştirici sayfası gösterir. |

Ürün sitesi burada **değil** — o ayrı repoda: [`dd-budget`](https://github.com/sehapps/dd-budget) → `https://sehapps.github.io/dd-budget/`

---

## Neden app-ads.txt ayrı bir repoda?

`app-ads.txt`, IAB standardı gereği **geliştirici web sitesinin alan adı kökünde** sunulmak
zorundadır. AdMob, Play Store kaydındaki web sitesi adresini alır, alan adının köküne gider ve
şu adresi tarar:

```
https://sehapps.github.io/app-ads.txt
```

Ürün sitesi `sehapps.github.io/dd-budget/` alt klasöründe olduğu için dosyayı oraya koymak
**işe yaramaz** — tarayıcı alt klasöre bakmaz. `github.io` Public Suffix List'te olduğundan
`sehapps.github.io` başlı başına bir kök alan adı sayılır ve kökü ancak hesap adıyla aynı isme
sahip bu repo (GitHub "user site") sunabilir.

> Gelecekte özel bir alan adı alınırsa bu gereklilik o alan adının köküne taşınır ve bu repo
> yalnızca geliştirici sayfası olarak kalabilir.

## Dosya bozulmamalı

- Düz metin olarak sunulmalı (`text/plain`), HTML'e sarılmamalı.
- Satır biçimi: `<reklam sistemi alan adı>, <yayıncı kimliği>, <DIRECT|RESELLER>, <sertifika kimliği>`
- Şu an tek satır var çünkü yalnızca **AdMob** kullanılıyor, mediation ağı yok.
  İleride mediation eklenirse **her ağ kendi satırını ister** — ağın dokümanındaki satırı aynen ekle,
  eksik satır o ağın talebini düşürür.

## Doğrulama

Yayına aldıktan sonra:

1. Tarayıcıda `https://sehapps.github.io/app-ads.txt` düz metin olarak açılmalı.
2. **Play Console → mağaza kaydı → Web sitesi** alanı `https://sehapps.github.io/dd-budget/`
   olarak girili olmalı (AdMob alan adını buradan çıkarır).
3. **AdMob → Uygulamalar → app-ads.txt** sekmesinde durum kontrol edilir.
   Google'ın taraması **24 saate kadar** sürebilir; hemen "bulunamadı" görmek normaldir.

## Yayınlama

Settings → Pages → Deploy from a branch → `main` / `(root)`.

---

© 2026 Sehapps
