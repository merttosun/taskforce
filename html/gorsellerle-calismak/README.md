# Görsellerle Çalışmak

Merhaba arkadaşlar bu yazıda HTML belgesine resim ekleme , bu resimlerle çalışma konusunu inceleyeceğiz.
Öncelikle HTML sayfasına resim eklemek için `<img>` tagi kullanılır. 

- ## Src=""
Kod bloğundaki **src=""** özelliğine resmin URL ya da dosya adresi belirtilerek resim HTML sayfasına çağırılır. (Resmi webden çağırmak için resmin URL'ini src=”…” parametesine eklemek yeterlidir.)

```html
<img src="ornek.jpg"/>
```

Yukarıdaki örnekte resim HTML dosyasıyla aynı dizinde olduğu için direkt adını ve uzantısını yazmak yeterlidir. Burada img uzantısına dikkat etmek önemli, HTML dosyaları nasıl **.html** ile bitiyorsa tüm resim dosyalarının sonu da **.xbm, .gif, .png veya .jpg** ile bitmelidir.

### Yaygın Image Formatları
Kısaltma | Dosya Formatı | Dosya Uzantısı
-- | -- | --
APNG	 | Animated Portable Network Graphics	| .apng
GIF	 | Graphics Interchange Format		| .gif
ICO		 | Microsoft Icon	| .ico, .cur
JPEG	 | 	Joint Photographic Expert Group image	| .jpg, .jpeg, .jfif, .pjpeg, .pjp
PNG		 | Portable Network Graphics	| .png
SVG		 | Scalable Vector Graphics	| 	.svg


Diyelim ki projenin içerisinde bir dizin oluşturdunuz (images) ve resminizi bu dizine eklediniz. Bu defa çağırmak için öncelikle images dizinine gitmek gerekiyor.

```html 
<img src="images/ornek.jpg"/> 
```

Ya da resim bir üst dizinde kalıyor olabilir. Bu durumda bir üst dizine çıkıp images dizinini bulup resmi çağırmak gerekiyor. (Üst dizine çıkmak için ../ kullanırız.)

```html
<img src="../images/ornek.jpg"/>
```

 Bu şekilde istediğiniz kadar üst dizine çıkabilirsiniz.
 
```html
<img src="../../images/ornek.jpg"/>
```
  
- ## Alt=""
Alt textlerin temel amacı, görüntüleri göremeyen kullanıcılar için metinler sunmaktır. Kullanıcı resmi görüntüleyemez ise (Yavaş bağlantı, src özelliğinde hata vb.) alt özelliği görüntü için alternatif bilgilendirici bir metin içerir.

```html 
<img src="../images/kedi.jpg" alt="Yavru Kedi"/>
```

- ## Title=""
Title özelliği kullanıcıyı bilgilendirme amacı taşır. Cursor ile resmin üzerine gelince bu özelliğe verilen text mesajı görünür. Ek açıklama gerektirecek resimlerde kullanabiliriz. Bilgilendirme amacı taşır.

```html
<img src="../images/kedi.jpg" title="image"/>	
```

**NOT**: _Title ve Alt parametreleri SEO açısından önem taşımaktadır._

- ## Width ve Height
Resme istenen ölçüleri vermek için width ve height özellikleri kullanılır. **Width yatay genişlik, Height ise dikey uzunluk** için kullanılır.Width ve Height özellikleri tanımlanmadığı zaman resim sayfada gerçek ölçüleri ile görünür. Bu ölçülerden yanlızca birine değer verildiğinde  resim oranları korunarak belirlenen ölçüde görünür. Her iki özelliğe de değer verildiğinde resim oranları yeni verilen ölçülerde olduğu gibi görünür. Bu kullanım resim ölçüleri ile uyumlu olmadığı zaman resimde oransal bozukluklar oluşur.

```html
<img src="resim.jpg" width="300" />
<img src="resim.jpg" height="400" />
<img src="resim.jpg" width="300" height="600" />
<img src="resim.jpg" height="100%" />

```
[Buradan](https://jsfiddle.net/detfj6w9/4/) örneği inceleyebilirsiniz.

- ## Border 
Resmi belirtilen kalınlıkta çerçeve içine alır. Daha gelişmiş CSS border özelliği bunun yerine kullanılabilir.
Border örneği: Resme 3 pixel kalınlıkta border verir.

```html
<img src="resim.jpg" border="3" />
```

- ## Align
Web sayfasında resmin gözükeceği pozisyonu belirlemede align özelliği kullanılır. Bu özelliğe verilebilecek değerler şunlardır: left, right. Resmin sağa veya sola yaslı çıkmasını sağlar.

```html 
<img src="resim.jpg" align="right" />
```

- ## Resme Link Vermek
Resme link vermek için img tagi a taginin içerisinde kullanılır. Yönlendirilmek istenen yerin URL'i a taginin href özelliğine yazılır.

```html
<a href="default.asp">
  <img src="smiley.gif" alt="HTML tutorial" style="width:42px;height:42px;">
</a>
```
[Buradan](https://jsfiddle.net/qcpfsev7/2/) örneği inceleyebilirsiniz.

- ## Map ve Area 
Resimlerinize hyperlink atamanız durumunda resmin tüm alanı link alanı haline dönüşecektir. Resmin herhangi bir yerine tıklanılması durumunda resim sizi tanımlanan bağlantıya gönderecektir. <img> etiketleri için kullanılan <map> ve <area> etiketleri ile resmin içindeki koordinatlarla belirlediğimiz bir alanı sadece link haline getirebiliriz. Eklediğimiz <area> etiketi kadar belirlenen alanı bir resim üzerinden birçok bağlantıya link verebiliriz.
 
 ```html
<html>
<body>
<img src="workplace.jpg" alt="Workplace" usemap="#workmap" width="400" height="379">

<map name="workmap">
  <area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.htm">
  <area shape="rect" coords="290,172,333,250" alt="Phone" href="phone.htm">
  <area shape="circle" coords="337,300,44" alt="Cup of coffee" href="coffee.htm">
</map>
</body>
</html>
 ```
 [Buradan](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_images_map2) inceleyebilirsiniz. 

- ## Onload event
Bu olay resim yüklenmesi tamamlandığında çalışacak fonksiyonu belirler. Herhangi bir nedenle resim yüklenemezse ya da belirtilen adreste resim yoksa fonksiyon çalışmaz.

```javascript
<html>
    <body>
        <img src="resim.jpg" onload="resimYuklendi()" />
    </body>
    <script>
        function resimYuklendi(){
            alert("Resim yüklendi.");
        }
    </script>
</html>
```

- ## Picture Elementi ile Kullanım
HTML5 ile gelen picture elementi web sayfamızda responsive imageler kullanmamız konusunda büyük kolaylıklar sağlıyor. Bir tane img ve birden fazla source içerebilir. Picture tagi ekran boyutlarına göre birden çok source kulllanmamızı sağlar bu sayede ekran boyutu değiştikçe image değişimi yapılabilir. Kod bloğu örneği: 

```html
<picture>
    <source srcset="https://cdn.sanity.io/images/9kdepi1d/production/65c832d202a503b15d99e628f4313782f3ef50db-300x62.png"
            media="(min-width: 800px)">
    <img src="/media/cc0-images/painted-hand-298-332.jpg" alt="" />
</picture>
```
Tarayıcı, her bir source öğesini inceleyip eşleşme sağlar. Eşleşme bulunamazsa veya tarayıcı `<picture>` öğesini desteklemiyorsa, `<img>` öğesinin src URL'si seçilir. Seçilen görüntü daha sonra `<img>` öğesinin kapladığı alanda sunulur.
  
[Buradan](https://jsfiddle.net/a2dvm503/4/) ekran boyutunuzu değiştirerek inceleyebilirsiniz. 


## Çoktan Seçmeli Sorular ##
- Resmimize link vermek için hangi özellik kullanılır? 
1. src
2. title
3. href
4. link


- Resmimize çerçeve eklemek istiyorsak hangi özelliği kullanmamız gerekir? 
1. align
2. round
3. border
4. width


- Image yolumuzu yazarken bir üst dizine nasıl çıkarız? 
1. /.
2. ./
3. ../
4. //

- Hangisi bir image formatı değildir? 
1. svg
2. ico
3. png
4. ogg



### Cevaplar ###
İlk sorunun cevabı href,
ikinci sorunun cevabı border,
üçüncü sorunun cevabı ../ , 
dördüncü sorunun cevabı ogg


_Kullandığım Kaynaklar: [1](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img) ,  [2](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/picture) , 
[3](https://www.w3schools.com/tags/tag_img.asp) , [4](https://notpast.com/html/HTML-Resim-Ekleme-83.html) , [5](https://www.m5bilisim.com/webokulu/etiketler/ozellik-img-alt.php)_
 
 






