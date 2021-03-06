# CSS Kutu Özellikleri(Margin, Padding, Width, Height) Kullanımı
CSS kutu özelliklerini iyi kavrayabilmek ve kullanabilmek için "kutu model" konusunu incelemek gerekir. Gelin önce "kutu modeli" konusuna bakalım.
## CSS Kutu Modeli 
![box](figures/box.png)
Resimde [Kodluyoruz'un anasayfasını](https://kodluyoruz.org) görüyoruz. İşaretlediğim alanlar birer HTML elementleri ve bir yapıyı oluşturan lego parçalarından sadece birkaçı. Kutu denmesinin sebebi de bir bütünü oluşturan lego parçaları veya kutu gibi olması. Bu kutuların aralarında mesafelerin ve içeriklerinin de kendi aralarında bir düzen olduğunu görmekteyiz. Bunun sebebi "kutu özelliklerinin" kullanılıyor olması. Özellikle yeşil kutuların içindeki yazıların belli bir mesafede olmasından ve çizdiğim yeşil hatlara değmemesinden anlayabiliriz. Burada kutu modelini şema halinde göstereceğim:

![boxmodel](figures/boxmodel_.png)

Kutu modeli margin,padding,border ve içerikten oluşur.
- İçerik(content): Elementin içinde olan resim,ses ya da yazıdır.
- Padding: İçerik ile border arasında olan boşluk.
- Border: Padding ile margini ayıran sınırdır. 
- Margin: Kutunun diğer kutularla arasındaki mesafeyi ayarlayan boşluk.

Yukarıda saydığım kavramların dışında kutunun boy ve uzunluğunu belirleyen width ve height kavramları vardır. Bunları da alıştırmalarımızda göstermeye çalışacağım.
## CSS Width ve Height
Width ve height özellikleri ile elementin,yani lego parçamızın boy ve genişliğini ayarlayabiliriz. Bu özellikleri biz yazmadığımız takdirde tarayıcı kendisi ayarlar ve yapacağımız web uygulamasında istenmeyen sonuçlara neden olur :)  Bu özellikleri px,em veya % ile kullanabiliriz. % ile kullandığımız zaman elementimiz hangi elementin içindeyse ona göre oranlanır. Yani 800px boyunda bir <div> tagının içinde bulunan bir elementin boyunu 50% olarak ayarlarsanız elementin boyu 400px olur. Max-width özelliği ise bir elementin genişliğini sınırlamak istediğimizde kullanırız. Diyelim ki bir element tarayıcı ekranından fazla geniş veya uzun. Bu durumda scrollbar(kaydırma çubuğu) çıkar. 

### Alıştırma-1: Width ve Height Kullanımı
```<style>
   p{
   width: 0;
   height: 0;
   }
   <style>
   <p>
   Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
   </p>
```
Bu kodda width ve heighti 0 yaptım. Paragraf tuhaf bir şekilde görünecektir. Bu alıştırmada yapmanız gereken şey paragrafın düzgün görünmesi açısından width ve heighti istediğiniz şekilde kullanın. Burada width ve heigthi görmeniz için % ve px in ikisini de kullanmanızı tavsiye ediyorum. Alıştırmaya [buradan](https://codepen.io/hyperborean17/pen/xxEXjYY) ulaşabilirsiniz. 


## CSS Margin ve Padding
Margin özelliği ile elementin dışında boşluk oluşturmada kullanıldığını öğrenmiştik. Şimdi nasıl kullanıldığını açıklamaya çalışacağım. Margin özelliğini 50px yaptığınızda elementin dört yanında 50px boşluk oluşturulur. Element sağa doğru kayar. Negatif değerler de kullanılır. Margin değerine -50px yazdığınız takdirde element sola doğru kayacaktır. Dört yanında değil de sadece bir yönde boşluk oluşturmak isteyebilirsiniz. Bunun için de özellikler vardır. 
- Margin-left: Soldan boşluk bırakır.
- Margin-top: Yukarıdan boşluk bırakır.
- Margin-bottom: Aşağıdan boşluk bırakır.
- Margin-right: Sağdan boşluk bırakır.

Bu değerleri tek bir satırda ayarlamanız mümkündür. 
```
margin: 100px 150px 60px 50px;
```
Bir elementi ortalamak için margin:auto değeri vermelisiniz. Bunun düzgün çalışması için de width öelliğinin de kullanılmasını öneririm. Böylelikte sağdan ve soldan eşit olarak ortalanmış olur.

Şimdi gelelim padding özelliğine. Elementin içindeki yazıların çerçeve(border) ile mesafesini padding ile ayarlarız. Margin özelliğinde olduğu gibi padding:50px yaptığımızda içeriğin her tarafı için 50px boşluk bırakıyoruz. Belirli bir tarafta padding bırakmak için;
-padding-top: içeriğin yukarısında boşluk bırakır.
-padding-bottom: içeriğin aşağısında boşluk bırakır.
-padding-left: içeriğin solunda boşluk bırakır.
-padding-right: içeriğin sağında boşluk bırakır.

Bunları tek tek tanımlamak yerine tek bir satırda belirlemek mümkündür. 

```
padding: 10px 20px 30px 40px;
<!---Burada üst boşluk 10px,sağ boşluk 20px,alt boşluk 30px ve sol boşluk 40px dir--->
```

```
padding: 10px 20px 30px;
<!---Üst boşluk 10px,sağ ve sol boşluk 20px,alt boşluk 30px dir--->
```
```
padding: 10px 20px;
<!---üst ve alt boşluk 10px,sağ ve sol boşluk 20px--->
```
Şimdi ikinci alıştırmaya geçelim.

### Alıştırma 2-Kutu Özelliklerinin Kullanımı

[Alıştırma için buraya tıklayın. Açıklama satırlarında ne yapmanız gerektiğini söyledim.](https://codepen.io/hyperborean17/pen/yLaKpJR)

## Sorular

* [Hangisi içeriğin aşağısında boşluk bırakır?]
  * bottom-padding: 20px;
  * padding: 0 20px 0 0;
  * padding-bottom: 20px; (Doğru)
  * padding: 20px;
* [Hangisi kutu modeline ait bir kavram değildir?]
  * margin
  * align (Doğru)
  * padding
  * border
  
## Kaynakça
- [1](https://css.sitesi.web.tr/css-kutu-modeli.html)
- [2](https://www.yazilimkodlama.com/web/css-kutu-modeli-margin-border-padding-content/)
- [3](http://uzmanimakademi.net/css/css-kutu-modeli)


