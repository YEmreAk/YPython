---
description: >-
  Satır satır çalıştırılan kodlar yerine isteğe göre çalıştırılan kodların nasıl
  yazılacağı.
---

# 💫 Thread ve MultiProcessing

## 🌅 Thread

{% tabs %}
{% tab title="❔ Nedir" %}
Thread ile satır satır ilerleyen kod yerine karma ilerleyen kodlar yazılabilir.

* `threading` modülü kullanılır
* Eş zamanlı işlemler için [multiprocessing]() tercih edilir

| Class | Açıklama |
| :--- | :--- |
| Thread | Sırasız olarak bir fonksiyonu çalıştırma |
| Timer | Belirli saniyelerde fonksiyonu çalıştırma |
| Scheduler | Bir plana göre fonksiyonu çalıştırma |
{% endtab %}

{% tab title="🧱 Yapısı" %}
```python
import threading

def ela(fname, orig_dir, save_dir):
    """
    Paremetreli bir fonksiyon
    """
    pass

dirc = "Dizin"
for d in os.listdir(dirc):
    if d.endswith(".jpg") or d.endswith(".jpeg"):
        thread = threading.Thread(target=ela, args=[d, dirc, ela_dirc])
        threads.append(thread)
        thread.start()

# Join edilmez ise, arka planda çalışır, print yazısından sonra bitebiebilir
# Join edilirse threadlerin tamamlanmasını beklemiş oluruz.
for t in threads:
    t.join()

print("Finished!")
```
{% endtab %}

{% tab title="💫 Tekrarlamalı" %}
```python
from time import sleep
from threading import Thread

def tekrarla(ne, bekleme):
    while True:
        print ne
        sleep(bekleme)

if __name__ == '__main__':
    dum = Thread(target = tekrarla, args = ("dum",1))
    tis = Thread(target = tekrarla, args = ("tis",0.5))
    ah = Thread(target = tekrarla, args = ("ah",3))

    dum.start()
    tis.start()
    ah.start()
    
# dum
# tis
# ah

# tis
# dumtis

# tis
# dumtis

# tis
# ah
# tisdum
```
{% endtab %}

{% tab title="⏱ Zamanlayıcı" %}
```python
import threading


def run_check():
    print("Fonksiyon çalıştı.")
    threading.Timer(5.0, run_check).start()


run_check()
```
{% endtab %}

{% tab title="🎌 Planlı Çalışan" %}
```python
import sched, time
s = sched.scheduler(time.time, time.sleep)
def do_something(sc):
    print "Doing stuff..."
    # do your stuff
    s.enter(60, 1, do_something, (sc,))

s.enter(60, 1, do_something, (s,))
s.run()
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Python'da eş zamanlı işler `thread` ile yapılamaz \([kaynak](https://stackoverflow.com/questions/7207309/python-how-can-i-run-python-functions-in-parallel/7207336#7207336)\)
{% endhint %}

## 🌃 Paralel İşlemler \(MultiProcessing\)

{% tabs %}
{% tab title="⭐ Örnek" %}
```python
from multiprocessing import Process


def func1():
    print('func1: starting')
    for i in range(10000000):
        pass
    print('func1: finishing')


def func2():
    print ('func2: starting')
    for i in range(10000000):
        pass
    print ('func2: finishing')


if __name__ == '__main__':
    p1 = Process(target=func1)
    p1.start()
    p2 = Process(target=func2)
    p2.start()
    p1.join() # Threadi çalıştırma (gecikmesini engellemek için)
    p2.join()

# func1: starting
# func2: starting
# func2: finishing
# func1: finishing
```
{% endtab %}
{% endtabs %}

