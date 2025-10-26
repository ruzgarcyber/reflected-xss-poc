# Reflected XSS PoC

## Açıklama
- Minimal, eğitim amaçlı Reflected XSS Proof‑of‑Concept.
- Bu dosyayı **sadece** izinli laboratuvar / VM / test ortamlarında çalıştırın.

## Gereksinimler
- Python 3.8 veya üzeri
- `requests` kütüphanesi
```bash
pip install requests
```
## Kullanım
```bash
python exploit.py --target http://10.10.10.10:8000 --endpoint /search --param q --debug --delay 1
```

## Ortak Seçenekler
- --target : temel URL (ör. http://host:8000)
- --endpoint : hedef endpoint yolu (ör. /search)
- --param : yansıtılan GET parametre adı (varsayılan: q)
- --payloads : özel payload'lar (boşlukla ayrılmış)
- --delay : istekler arası bekleme süresi (saniye, varsayılan: 1)
- --debug : detaylı istek/çıktı gösterimi
- --deterministic : deterministik davranış (tek UA, tekrarlanabilir)
- --no-ua-rotation : User-Agent rotasyonunu kapat

## Öne çıkan özellikler (PoC ile eşleşir)
- Okunaklı terminal çıktısı: [BİLGİ], [BAŞARILI], [UYARI], [HATA].
- Sağlam tespit: doğrudan, HTML‑escaped, URL‑encoded ve regex kontrolleri.
- Kayıt: tüm denemeler results.jsonl içine time‑stamped JSON satırları olarak kaydedilir.
- Esneklik: varsayılan payload'lar mevcut, ek payload verebilirsiniz.
- **Ek/özel payload'lar eklemek için --payloads kullanın.**

## Güvenlik & notlar
- Sadece kendi sahip olduğunuz veya açıkça izin aldığınız hedeflerde çalıştırın.
- Bu repo eğitim amaçlıdır; kötüye kullanım yasaktır.
- **results.jsonl** içinde test çıktıları bulunur — commit etmeden veya paylaşmadan önce dosyayı kontrol edin.
