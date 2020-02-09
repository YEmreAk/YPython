---
description: Python ile virtual environment oluşturma (venv)
---

# 🌇 Sanal Ortam Oluşturma

## 🚴‍♂️ Sanal Ortama Giriş

* 🌇 Sanal ortamlar ile python paketleri ve sürümlerinin çakışması engellenir
* 🦄 Her projeye özgü bir python ortamı kullanılır
* 📈 Verimliliği artırır

```bash
# Sanal ortamı kurma
python3 -m venv tutorial-env
```

## 🐣 Sanal Ortamı Aktif Etme

* 💁‍♂️ Eğer [VS Code](https://code.visualstudio.com/) kullanıyorsanız, otomatik olarak aktif edilecektir

{% tabs %}
{% tab title="✴️ Windows" %}
```text
tutorial-env\Scripts\activate.bat
```
{% endtab %}

{% tab title="🐧 Linux / MacOS" %}
```text
source tutorial-env/bin/activate
```
{% endtab %}
{% endtabs %}

## 🔗 Faydalı Bağlantılar

{% embed url="https://docs.python.org/3/tutorial/venv.html" %}



