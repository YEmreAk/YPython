# ✨ Faydalı İşlemler

## 📑 PDF İşlemleri

PDF işlemleri için pdfkit modülü kullanılır.

* `pip install pdfkit` ile modülü indirin
* Modül için gerekli [wkhtmltopdf](https://github.com/wkhtmltopdf/wkhtmltopdf/releases) aracını indirin
* İndirdiğiniz aracın içerisindeki `wkhtmltopdf.exe` dosyasının yolunu bulun
  * İleride yapılandırma ayarı için kullanılacaktır
* İşlemler sırasında python kodunun çalıştırıldığı yola dikkat edin

> Farklı bir modül için [buraya](https://towardsdatascience.com/python-for-pdf-ef0fac2808b0) bakabilirsin

```python
import pdfkit

path_wkthmltopdf = r'C:\Program Files\wkhtmltopdf\bin\wkhtmltopdf.exe'
config = pdfkit.configuration(wkhtmltopdf=path_wkthmltopdf)

pdfkit.from_file('file.html', 'out.pdf', configuration=config)
```

## 📊 İstatistiksel İşlemler

{% tabs %}
{% tab title="Median Alma" %}
```python
import statistic
```
{% endtab %}

{% tab title="Medyan Filtre" %}
```python
final = cv2.medianBlur(source, 3)
```
{% endtab %}
{% endtabs %}

## 🎴 Görüntü İşlemleri

{% tabs %}
{% tab title="🔂 Resmi np.array Yapmak" %}
```python
# OpenCV ile alırsak resim numpy formatında olur
import cv2
im = cv2.imread("abc.tiff",mode='RGB')
print type(im)
```
{% endtab %}

{% tab title="📊 Histogram Germe İşlemi" %}
```python
def histogram_stretching(image: Image, new=(0, 255)):
    """Histogram Germe

    Arguments:
        image {PIL.Image} -- Resim

    Keyword Arguments:
        new {(min, max)} -- tuple (default: {(0, 255)})

    Returns:
        PIL.Image -- Gerilmiş resim
    """

    def difference(variable: tuple):
        return variable[1] - variable[0]

    np_image = np.array(image)  # Resmi numpy.ndarray formatına çevirme
    flatten_img_np = np_image.reshape(-1)  # Resmi tek boyuta indirgeme

    # Histogram germe denklemi
    old = flatten_img_np.min(), flatten_img_np.max()
    for i in range(0, len(flatten_img_np)):
        flatten_img_np[i] = (difference(new) / difference(old)) * \
            (flatten_img_np[i] - old[0]) + new[0]

    # Aynı boyutlardaki yeni resmi oluşturma
    return Image.fromarray(flatten_img_np.reshape(np_image.shape))    
```
{% endtab %}

{% tab title="📊 Histogram Eşitleme" %}
```python
def histogram_equalization(image: Image):
    """Histogram eşitleme

    Arguments:
        image {PIL.Image} -- Resim

    Returns:
        PIL.Image -- Resim
    """

    np_image = np.copy(image)  # Numpy formatına çevirme
    flatten_image = np_image.flatten()  # Resmi tek boyuta indirgeme

    # Pixel bilgilerini alma
    pixel_num = len(flatten_image)
    max_pixel_num = flatten_image.max()
    min_pixel_num = flatten_image.min()

    # Pixel dağılımını hesaplama
    pixel_manager = {}  # Pixel yönlendirici
    cumulative_probability = 0  # Kümülatif pixel bulunma olasılığı
    for i in range(min_pixel_num, max_pixel_num + 1):
        pixel_count = 0  # Pixel'in tekrar etme sayısı
        for pixel in flatten_image:
            if i == pixel:
                pixel_count += 1
        cumulative_probability += pixel_count / pixel_num
        pixel_manager[f'{i}'] = round(
            max_pixel_num * cumulative_probability
        )

    for i in range(len(flatten_image)):
        flatten_image[i] = pixel_manager[f"{flatten_image[i]}"]

    return Image.fromarray(flatten_image.reshape(np_image.shape))
```
{% endtab %}

{% tab title="🔗 Diğer Bağlantılar" %}
* [Noise filtering in Digital Image Processing](https://medium.com/image-vision/noise-filtering-in-digital-image-processing-d12b5266847c)
* [İki resmi birleştirme](https://stackoverflow.com/a/29108632/9770490)
* [Matplotlib resim işlemleri](https://matplotlib.org/3.1.1/tutorials/introductory/images.html)
{% endtab %}
{% endtabs %}

