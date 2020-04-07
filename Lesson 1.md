# Lesson 1 

### Başlıklar: 
* Sosyal Fayda için Veri Bilimi nedir ?
* Programın gidişi ve program sonundaki projeler 
* Neden R ?
* R ve R studio Yüklenmesi
* Giriş 
* Veri tipleri
* R objeleri oluşturma
* Mantıklsal Öpretarörleri
* Vektörler
* Matrisler
* Faktörler
* Dataframeler
* R notasyonları
* R'da Listeler

# Giriş:
R, S programlama dili üzerine yazılan ve istatistiksel analizlerin R içindeki kütüphaneler yardımıyla 
kolay bir şekilde yapılmasını sağlayan bir platformdur. 
R studio, R dilini Compile etmek için kullanacağımız araçtır. 

R studio içinde dört tane kısımdan oluştuğunu görüyoruz,
* Sol üst kısım, kod yazacağımız kısımdır
* onun altında Console yer almaktadır, yazdığımız kodun çıktısı burada görebiliriz
* Sağ üst kısım Environment kısmı, compile edilen değişkenler burada görünyor
* onun altında Help kısmı, R studio da bir şeyi aratmak istediğimizde kullanırız


R'ı başlangıçta bir hesap makinesi olarak düşünebiliriz, burada her türlü hesaplar yapabiliriz. Toplama, Çıkarma ve Çarpma işlemleri görelim. 

**NOT: yazdıklarımızı çalıştırmak için ya üzerine işaretleyip yukarıdaki *run* tuşuna tıklayıp ya da kısaca CTRL+ENTER basabiliriz**
```R
#Toplama
3452 + 3452
> 6904

#Çıkarma
15-70
> -55

#Çarpma
15 * 22
> 330
```

Bölme işlemi bildiğimiz bölme sembölü (%) ile de deneyelim, 
```R
#Bölme
5%2
> Error: unexpected input in "5%2"
```
Bir hata aldık! hatayı okuyalım, "Error: unexpected input in "5%2"" diyor, yani beklenmedik bir sembolü okuduğunu söylüyor 
R'da bölme işareti '%' ile gösterilmez, '/' sembölü ile gösterilir.

> *İnan Hoca: Hataları okumayı öğrenmemiz lazım, sürekli hatalarla karşılaşacağız ve onları okuyup hatayı gidermeye çalışacağız.*

  ## Veri tipleri
  R'da bir sürü veri tipleri vardır, bunlara bakalım:
  * Character : Text ifadeleri character tipinden olur
  ```R
  "CADS DPSG"
  "TEDU"
  ```
  * Numeric: Decimal sayılar numeric tipindendir
  ```R
  12.5
  20
  ```
  * Integers: Doğal sayılara İnteger diyoruz, integer sayılar numeric sayılır.
  Integer sayıları ayırt etmek için ardından L harfi ekleyebiliriz
  ```R
  5L
  > 5
  ```
  
  * Logical (Mantıksal): Mantıksal operatörler R’da TRUE ve FALSE ile ifade edilmektedir. Bir ifadenin doğruluğunu veya yanlışlığını       belirlemek amaçlı kullanılır. Aynı zamanda, TRUE 1 rakamına eşit olup FALSE ise 0 rakamına eşittir.
  R’da Mantıksal operatörler veriyi manipüle etmede (filtreleme, veriden kesit alma, döngüler) oldukça önemli ve kullanışlıdır.
  ```R
  TRUE
  > TRUE
  
  FALSE
  > FALSE
  
  T
  > TRUE
  
  F
  > FALSE
  ```
  
  R'da TRUE ifadesi 1 olarak, FALSE ifadesi 0 olarak algılanır. Bunu şu şekilde görebiliyoruz
  ```R
  TRUE + TRUE
  > 2
  
  FALSE + FALSE
  > 0
  
  TRUE + FALSE 
  > 1
  
  TRUE == 1
  > TRUE
  
  FALSE == 0
  > TRUE
  ```
  **NOT: Bir karşılaştırma yapmak istersek "==" ifadesini kullanıyoruz. "=" atama ve fonksiyon argümanlarında kullanılan bir semboldür.**
  
  * Complex: kompleks ifadeleri çok kullanacak olmasak bile, varlığından bilmekte fayda var.
  ```R
  1+2i
  ```
  
  Farklı tiplerden veri toplarsak ne olur ?
  ```R
  16 + TRUE
  > 17
  
  12 + "12"
  > Error in 12 + "12" : non-numeric argument to binary operator
  ```
  12 + TRUE ifadesini toplayabildi çünkü daha önce gördüğümüz gibi TRUE ifadesi 1 olarak algılanır. Yalnızca 12+"12" ifadesi bir hata verdi çünkü tırnak içinde yazdığımız herhangi bir şey character olarak algılanır, sayı olarak değil. 
  
  Bir şeyin veri tipini incelemek istersek **class()** fonksiyonu kullanabiliriz,
  ```R
  class(12)
  > numeric
  
  class("12")
  > character
  
  class(TRUE)
  > logical
  
  class("TRUE")
  > character
  ```
  
  ## R objeleri oluşturma
  R'da bazı fonksiyonlar objelerle çalışır. Dolayısıyla bir fonksiyonun çalışması için obje oluşturma (değişken atama)
  yapmamız gerekir. Bunu "<-" veya "=" sembolleriyle yapabiliriz. Fakat "=" başka işlemlerle de kullanıldığı için
  genelde "<-" sembolü kullanarak atama yapmayı tercih edebiliriz.
  
  Bir character değişkeni oluşturalım:
  ```R
  x <- "Data Science For The Public Good"
  ```
  "Data Science For The Public Good" ifadesini tanımlayıp x adlı değişkenine atadık. R studio'nun Environment kısmına bakarsak x' in yer    aldığını görürüz. Şimdi x değişkenini ne zaman istersek çağırarak değerini elde edebiliriz.
  ```R
  x
  > "Data Science For The Public Good"
  ```
  
  Bir numeric değişken oluşturalım,
  ```R
  a <- 5
  b <- 6
  c <- a+b
  c
  
  > 11
  ```
  
  **NOT: dikkat edelim ki R studionun environment kısmında compile ettiğimiz değişkenlerin bilgileri yer almaktadır.**
  
  > **Egzersiz:  numerik1 ve numerik2 objelerine (değişkenlerine) 4 ve 2 rakamlarını atayıp bu iki objei toplayalım. Bu toplamı "numeriklerim" isimli değişkene atayıp verinin tipini inceleyelim.**
  
  > **Egzersiz: a'nın 10 b'nin 2 olduğu iki numerik değişken oluşturalım. Bu iki değişkeni çarptıktan sonra c isimli değişkene atayalım. Sonrasında ise c'nin b üstünü (^) sembolü kullanarak alalım.**

  
  ## Vektörler: 
  R vektörleri aynı tip elemanlardan (veriden) oluşan bir koleyksiyondur. Bir vektör sadece aynı tip elemanlara sahip olabilir. 
  İleride işlenecek olan değişken ve Data Frame konularında değişkenleri oluşturmada kullanılır. 
  Bir vektör "c()" fonksiyonu ile oluşturulur.
  
  ```R
  vektörüm <- c("Hello","World")
  vektörüm
  
  >"Hello"  "World"
  
  class(vektörüm)
  > "character"
  ```
  
 > **Egzersiz: vektorum1 isimli ve elemanları "DSPG", "CADS", "TEDU" olan bir vektör oluşturalım. sonrasında isi genelvektor isimli   vektörümüzü vektorum ve vektorum1 vektörlerini kullanarak oluşturalım.**
 
 Numerik Vektör oluşturalım:
 
 ```R
 numerik_vek1 <- c(1,2,3,4,5)
 numerik_vek2 <- c(6,7,8,9,10)
 class(numerik_vek1)
 > "numeric"
 
 toplam_vek <- numerik_vek1 + numerik_vek2
 toplm_vek 
 > 7  9 11 13 15 
 
 toplam_vek <- toplam_vek + 1
 toplam_vek
 > 8 10 12 14 16
 ```
 
 Belli bir aralıkla bir sayı vektörü oluşturmak istersek:
 ```R
 benim_vektorum <- 1:10
 benim_vektorum
 > 1  2  3  4  5  6  7  8  9 10
 ```
 seq() fonksiyonu da kullanabiliriz. 
 ** NOT: fonksiyonun adından önce '?' işareti koyup ( ?seq() şeklinde ) çalıştırırsak sağdaki pencerede fonksiyonun tanımı, aldığı parametreler, ve diğer kullanım bilgileri bulabiliriz. En ağağıya gelirsek örnekleri de bulabiliriz  **

```R
aralıklı <- seq(from=1, to=10, by=2)
aralıklı

> 1 3 5 7 9
````
  
**Egzersiz: Kiloları 65, 70, 80, 90, ve 100 olan, boyları ise 1.65, 1.75, 1.85, 1.9, ve 2.0 olan öğrencilerin kilo ve boy isimli vektörlerini oluşturalım. Ayrı ayrı hem kilo hem boy ortalamalarını bulalım.
İpucu: Vektörler oluşturulduktan sonra mean() fonksiyonun içine oluşturduğumuz vektör isimlerini yazarak ortalamaları bulabiliriz.**

```R
kilo <- c(65, 70, 80, 90, 100)
boy <- c(1.65, 1.75, 1.85, 1.9, 2)

mean(kilo)
mean(boy)

> 81
> 1.83
```