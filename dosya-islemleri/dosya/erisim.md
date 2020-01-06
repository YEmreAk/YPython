---
description: Dosya işlemlerinde erişim işlemleri
---

# 👮‍♂️ Dosyaya Erişim

## ✨ Kullanım

* Python üzerinde dosya işlemleri oldukça kolaydır.
* Temel okuma metodu `open(<dosya_ismi>, <erişim_modu>, encoding=<kodlama>)` şeklindedir
  * `<dosya_ismi>` Dosya yolu veya ismi
    * _Örn: "text.txt"_
  * `<erişim_modu>` Okuma, yazma veya ekleme
    * _Örn: 'a', 'w', 'r', 'r+' ..._
  * `<kodlama>` Dosya kodlama formatı
    * _Örn: 'utf-8'_
* Dosya bulunamazsa `IOError` hatası verir

## 💎 Erişim Modları

| Mod | Anlamı | Açıklama |
| :--- | :--- | :--- |
| `r` | Read \(Okuma\) | Dosya varsa okumak için açar yoksa hata verir |
| `w` | Write \(Yazma\) | Dosyayı sıfırdan yazmak için oluşturma \(verileri siler\) |
| `a` | Append \(Ekleme\) | Dosyayı üzerine eklemek için açar, yoksa oluşturur |
| `wb, rb, ab` | Binary işlemleri | Sıkıştırılmış dosyada işlemler |

> Ek bilgiler için [buraya](https://stackoverflow.com/a/1466036/9770490) bakabilirsin.

## 💠 İşlem Metodları

| Mod | Açıklama |
| :--- | :--- |
| `read()` | Dosyayı komple okuma |
| `readline()` | Dosyadaki 1 satırı okuma |
| `readlines()` | Dosyadaki tüm satırları `list` objesine alma |
| `write(<metin>)` | Dosyaya metin yazma |
| `close()` | Dosyayı kapatma \(context manager için gerekli değil\) |

## ⭐ Erişim Örnekleri

```python
file_str = ""
with open("README.md", "r", encoding="utf-8") as file:
    file_str = "".join(file.readlines())
```

```python
file_str = ""
with open("README.md", "r", encoding="utf-8") as file:
    for line in file:
        file_str += line
```

```python
with open(xml_path) as fp:
        for row, line in enumerate(fp):
            pass
```

```python
with open("README.md", "r", encoding="utf-8") as file:
    lines = list(file) # Tüm satırları liste olarak döndürür
    line = file.readline() # Tek bir satırı string olarak döndürür
    lines = file.readlines() # Tüm satırları liste olarak döndürür
```

