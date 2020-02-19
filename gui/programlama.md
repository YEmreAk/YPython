# 👨‍💻 Görsel Programlama

## 💠 Python görsel programlama araçları

* PyQt5
* Tkintrer \(zaten yüklü olarak gelir\)
* WxPython
* Kivy \(opensource\)
* PyForms

![](../.gitbook/assets/image.png)

## 📦 PyQT5

Python görsel programlama **PyQt API**'ı ile yapılmaktadır.

* Bu yazıyı oluştururken yararlandığım kaynak için [buraya](https://build-system.fman.io/pyqt5-tutorial) bakabilirsin.
* Türkçe eğitim serisi için [buraya](https://www.youtube.com/playlist?list=PLOl6SW8nLgJx9guRvfylVwrMXIginZhin) bakabilirsin.
* Hızlıca göz atmak için [buraya](https://www.youtube.com/watch?v=GLqrzLIIW2E) bakabilirsin

{% tabs %}
{% tab title="🚧 Kurulum" %}
GUI için _cross development_ desteği olan **pyqt** kullanılmaktadır.

* `pip install pyqt5`
* `conda install pyqt5`

> 💡 _Cross development_: Birden çok işletiim sisteminde çalışabilen yazılım geliştirmesi: PC, Mac, linux vs..
{% endtab %}

{% tab title="✨ GUI Yapımı" %}
GUI oluşturma yardımcı olan **QTDesigner** oldukça faydalı olacaktır. \(💡 Çek-bırak mantığında çalışır. \)

```python
from PyQt5.QtWidgets import QApplication, QLabel

# Uygulamayı tanımlama
# - [] objesi içine aktarılacak argümanları ifade eder
app = QApplication([])

# Pencernein içine yazı yazma ve görünür kılma
label = QLabel('~ YEmreAk')
label.show()

# Uygulamayı kullanıcı kapatana kadar çalıştırma (exec olursa arkaplanda da çalışır)
app.exec_()
```
{% endtab %}

{% tab title="💠 Widgets" %}
PyQT deki her bir obje widget olarak adlandırılmakta

![](../.gitbook/assets/image%20%284%29.png)

Yukarıdan-aşağı, soldan-sağa olmak üzere sırayla:

* [QLabel](http://doc.qt.io/qt-5/qlabel.html)
* [QComboBox](http://doc.qt.io/qt-5/qcombobox.html)
* [QCheckBox](http://doc.qt.io/qt-5/qcheckbox.html)
* [QRadioButton](http://doc.qt.io/qt-5/qradiobutton.html)
* [QPushButton](http://doc.qt.io/qt-5/qpushbutton.html)
* [QTableWidget](http://doc.qt.io/qt-5/qtablewidget.html)
* [QLineEdit](http://doc.qt.io/qt-5/qlineedit.html)
* [QSlider](http://doc.qt.io/qt-5/qslider.html)
* [QProgressBar](http://doc.qt.io/qt-5/qprogressbar.html)

> Ekran görüntüsündeki kodu [buraya](https://build-system.fman.io/static/public/files/widgets_example.py) tıklayarak indirebilirsin.
{% endtab %}
{% endtabs %}

## 🟢 QT \(PySide2\)

* 💰 Ticari kullanımlar için paralıdır
* 👨‍💻 OpenSource ve GPL lisanslı kodlar için ücretsizdir

{% embed url="https://www.qt.io/qt-for-python" caption="" %}

## ✨ Executable Dosya Oluşturma

{% tabs %}



{% embed url="https://github.com/brentvollebregt/auto-py-to-exe" caption="" %}

{% embed url="https://www.youtube.com/watch?v=lOIJIk\_maO4" caption="" %}

