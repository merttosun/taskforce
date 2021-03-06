# .gitignore Dosyası Ne İşe Yarar? Nasıl Kullanırız?

Konu .gitignore dosyasını araştırmaya kadar gelmişse daha öncesinde git ile tanıştığınızı varsayıyorum :) Tabi yine de kısaca bahsedelim. Git bir versiyon kontrol sistemidir. Geliştirdiğimiz projeleri ya da dosyaların güvenli ve düzenli bir şekilde korumak ve takip etmek istersek git tam da bunun için var. 
Konumuz dağılmadan gelelim .gitignore dosyasının maharetlerine .

.gitignore dosyası projemizin kök dizinine oluşturulan düz bir metin dosyasıdır. Adından anlaşıldığı gibi diyor ki beni göz ardı et. Daha doğrusu göz ardı etmek istediğin, local çalışma alanındaki takip edilmesini istemediğin, takım arkadaşların için gerekmeyen dosyaların varsa veya bu dosyaların boyutu reponuza atmanıza gerek olmayacak kadar büyük ölçekli ise buyur beni kullan diyor. Gel bu dosyaları .gitignore dosyasına koy ki git de senin bu dosyalarını artık takip etmesin. Üstelik bu işlemler yapılırken senin halihazırdaki dosyalarını da hiç bir şekilde etkilemesin. Daha ne olsun!

## Peki nedir bu tür dosyalar ? 

- Paket yöneticisinden indirilen bağımlılıklar,
- image ve video dosyalarınız(dosya boyutları çok fazla olabilir)
- IDE eklentileri( örneğin `.vscode`)
- Sadece kendi çalışma alanınızda olması gereken başkaları tarafından görülmemesi gereken dosyalarınız (veritabanınıza ilişkin konfigurasyonlar)
- API anahtarları, kimlik bilgileri veya hassas bilgiler içeren dosyalar(.env)
- Çalışma dizinizdeki geçici dosyalar
- Log dosyaları
- Yararsız sistem dosyaları (örneğin MacOS işletim sisteminin `.DS_Store` dosyası )
- `dist` gibi oluşturulan dosyalar
- Ve ya herhangi bir dosyanız da olabilir.

## Nasıl oluşturulur?

Reponuzu oluştururken verilen seçeneklerde add gitignore file dosyasına tıklayarak reponuzla beraber oluşturabilirsiniz. Aynı şekilde editörünüzde .gitignore şeklinde de oluşturabilirsiniz. 
Yok ben terminal aşığıyım diyorsanız da buyrun :)

Proje dizininize cd komutu ile gelerek 

MacOS /Unix için; 

```
$ touch .gitignore 
```

Windows için;

```
$ echo some-text or nothing > .gitignore
```

şeklindeki komutlarla dosyanızı komut satırından oluşturabilirsiniz. Buradaki `some-text or nothing` kısmı .gitignore dosyasına yazılmasını istediğiniz metini ekler . Hiçbir şey de yazmayabilirsiniz. 

## Nasıl  çalışır , nasıl kullanılmalı ?

.gitignore dosyasının her satırına takip edilmesini istemediğimiz dosyaları veya dizinleri yazarak göz ardı edebiliriz.

Tabi bu dosyaları yazarken bize kolaylık sağlayan bazı formatlar var.  İşte onlar ;

- En basit haliyle dosyamızın ismini ekleyebiliriz.

  ```
  .env
  ```

- Dizinleri ise klasörün sonuna `/` işareti ekleyerek  belirtiriz. 

  ```
  node-modules/
  dist/
  logs/
  ```

- `*` yıldız karakteriyle ise belirtilen ilk örnekte `.log` uzantısına sahip dosyaların tümünü, ikinci örnekte ise `files` klasör içerisindeki bütün dosyaları izlemeyi bırakacaktır. 

  ```
  *.log 
  files/*
  ```

- Eğer ki bir klasörümüzü içerisindeki bir dosya haricinde izlenmesini istemiyorsak `!` işareti ile bunu sağlayabiliriz. Bu örnekte `files` klasörü içerisindeki `example.txt` haricindeki dosyalar izlenmeyecektir. Files klasörü içerisindeki sadece example.txt git akışında görülecektir.

  ```
  !files/example.txt
  ```

- Yukarıdaki örnekte dikkat edilmesi gereken önemli bir ayrıntıyı açıklayacak olursak eğer ki daha öncesinde `files` klasörü .gitignore dosyasına eklenmişse sonrasında ise `!`  içerisindeki dosya ile işlem yapmak işe yaramayacaktır. 

  ```
  files/
  !files/example.txt
  ```

- .gitignore dosyasında yorum satırı oluşturmak için ise `#` karakteri kullanılır.

  ```
  # production
  /build
  
  # dependencies
  /node_modules
  ```



Kullanımından da bahsettiğimize göre gelelim dikkat edilmesi gereken hususlara...

## Neye dikkat etmeliyim?

- Eğer projenizi `git add .` veya `git commit ` etmişseniz sonrasında  .gitignore  dosyasına eklemek istediğiniz dosyayı ekleseniz de bu işlem gerçekleşmeyecektir ve o dosyanız reponuzda hala git ile takip edilecektir. Tabi her şeyin bir çözümü olduğu gibi bu sorunu da çözmenin bir yolu var. İşte o çözüm .

  ```
  $ git rm --cached FILENAME
  ```

- Hani olur da derseniz ben belli dosyalarımı her seferinde .gitignore dosyasına eklemek istemiyorum bunu tek seferde halledebilir miyim ? Tabi ki buna da bir çözüm bulmuş git babamız :)

- Windows kullanıcısı iseniz  `C:\Users\{myusername}\` adresine giderek  `.gitignore_global` dosyası oluşturup içerisine global olmasını istediğiniz dosyaları ekledikten sonra git bash terminalinizi açarak aşağıdakı komut ile konfigürasyon sağlayabilirsiniz. 

  ```
  $ git config --global core.excludesfile "%USERPROFILE%\.gitignore"
  ```

- Dosyanızın doğru çalıştığını kontrol etmek için ise aşağıdaki komutu çalıştırarak aşağıdaki çıktıyı aldığınızda sorunsuz çalıştırabilmişsinizdir.

  ```
  $ git config --global core.excludesfile
  > C:/Users/user-name/.gitignore_global
  
  ```

- Son olarak hangi .gitignore dosyalarını eklemeliyim derseniz 

  [burada]: https://github.com/github/gitignore

  hangi dil, framework vs kullanıyorsanız ona ait .gitignore dosyalarını bulabilirsiniz. Global olarak düzenlemek istediğiniz .gitignore dosyalarına da 

  [buradan]: https://github.com/github/gitignore/tree/master/Global

  erişebilirsiniz. 

  

Bana bunlar da yeterli değil diyorsanız buyrun bizzat yararlandığım bu linklerden siz de istifade ediniz :hugs:

https://docs.github.com/en/free-pro-team@latest/github/using-git/ignoring-files

https://www.pluralsight.com/guides/how-to-use-gitignore-file

http://git-scm.com/docs/gitignore

https://sebastiandedeyne.com/setting-up-a-global-gitignore-file/



## Sorular

1. `.dll`  uzantısına sahip bütün dosyaları .gitignore dosyasına eklemenin doğru kullanımı hangisidir? 

- [ ] `/.dll`
- [x] `*.dll`
- [ ] `-.dll`
- [ ] `!.dll`

2. Hangisi veya hangilerinde .gitignore 'a dosya eklerken doğru bir format kullanılmıştır?

- [ ] node_modules/
- [ ] .vscode
- [ ] !files/example.txt
- [x] Hepsi

3. gitignore dosyalarına hangi tür dosyalar konulabilir?

- [ ] Takip edilmesini istemediğimiz dosyalar 
- [ ] Apı key vb özel dosyalar
- [ ] Geçici dosyalar
- [ ] IDE eklentileri
- [x] Hepsi





