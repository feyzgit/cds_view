# CDS(Core Data Services) View

  Cds, Sap hana nın sağladığı değişimlerden, avantajlardan biridir.
Cds, veri modellerinin uygulama düzeyi yerine veri tabanı düzeyinde kullanılmasını ve tanımlanmasını sağlayarak performansı artırmayı amaçlar.

  Veri modelleri, veri tanımlama dili [DDL] ve veri kontrol dili[DCL] ne dayalıdır.

  Hananın en önemli getirisi veri işleme açısından, işlemeyi daha hızlı hale getirmek için veri tabanına direk erişim sağlaması ve ağ sebebiyle gelişebilecek gecikmeleri ortadan kaldırmasıdır.
Yoğun veri içeren işlemler  code to data paradigmasını kullanarak veri tabanı katmanının kendisinde gerçekleştirilir. Bu kodun işlenmek üzere aşağıya itilmesi anlamına gelir yani code push down denilmektedir. Böyle isimlendirmesinin sebebi ise, veriye ulaşma ve onu hazır etme işlemlerini uygulama sunucusu üzerinde yapmaktansa, veri tabanı seviyesine indirgemesi ve yükü veri tabanına vermesidir. 

![image](https://user-images.githubusercontent.com/76265899/202611456-918e2cfb-6d46-47f6-8cea-a6b3fdd3b939.png)

  Code pushdown, tüm verileri uygulama katmanına almak yerine kodu veri tabanı katmanına iten ve gerekli sonuç kümesini alan ve gerekli çıktıyı almak için kodu uygulama katmanına yazan bir paradigmadır.

#### CDS View Extension 

  CDS Viewler sanal veri modelleri olduğundan bir proje veya bir nesne için oluşturulan CDS View'ler başka bir proje veya nesne içinde kullanma ihtiyacı oluşacaktır. 
Örneğin SPFLI Tablosunun 5 alanını kullanarak bir CDS View oluşturduğumuzu ve başka bir proje için yine SPFLI Tablosunsun 3 alanına daha ihtiyaç duyduğumuzu varsayalım, bu durumda baştan CDS View oluşturmak yerine 'Extend View' seçeneği ile sahip olduğumuz CDS View'e ihtiyaç duyduğumuz alanları dahil edebiliriz. Extend View'lere sadece alan eklenebilir ve 'WHERE' yan tümcesini kullanılamaz.

![image](https://user-images.githubusercontent.com/76265899/202612936-6b5b5749-0c0c-4207-b0d2-2cf2ebc82598.png)

![image](https://user-images.githubusercontent.com/76265899/202613492-ee4ea526-f290-4fce-b104-58fac4768bb0.png)
![image](https://user-images.githubusercontent.com/76265899/202613538-f24fcccf-9272-4c62-a523-7dc8975ac003.png)

#### Fonksiyonlar

  Cds view lerde de kullanabileceğimiz bazı fonksiyonlar mevcut. Bunlar abap kodlarken kullandıklarırmızdan farklı değildir. Numeric ve string fonksiyonlar gibi birçok fonksiyonlardır. En sık kullandıklarımız concat, replace, substring gibidir.
  
  Cds de farklı olan fonksiyonlardan biri ise CURRENCY_CONVERSION.
  Elimizdeki tabloda para birimleri farklı olsa bile verdiğimiz parametredeki para birimine dönüşür.

![image](https://user-images.githubusercontent.com/76265899/202614248-3d8a5649-9329-4adc-8c93-8f3b2720271f.png)
### Se16n Görünümü
![image](https://user-images.githubusercontent.com/76265899/202614369-6ff76e39-7e93-4b49-a2f2-6c92ccaf98ff.png)

### Cds Görünümü
![image](https://user-images.githubusercontent.com/76265899/202614273-464a93d3-1733-421f-a0d8-e6e7ff86fa98.png)

  Bunlara ek alarak sql in sağladığı case when yapılarını ve aggregate fonksiyonları da kullanabilir. Bunlar max min avg sum count dır.

#### CDS View Parameters

  CDS View' lerde veri fitrelemek için 'WHERE' yan tümcesini kullanabiliriz. 'Parameters' özelliği ile veri fitrelemesi yapmak mümkündür.

![image](https://user-images.githubusercontent.com/76265899/202615091-0773ff8a-aa21-404e-99bd-6adcdf12271d.png)

#### CDS View Join

  CDS View'ler bir SQL geliştirmesi olup, projelerde verileri anlamlı bir bilgiye dönüştürmek için birden fazla tabloyu birleştirmemiz gerekebilir. CDS view ler de kullandığımız join türleri: 

-Inner Join
-Left Outer Join
-Right Outer Join

![image](https://user-images.githubusercontent.com/76265899/202615713-b26a66cf-88c7-4ed2-8db2-3b0412df8100.png)

![image](https://user-images.githubusercontent.com/76265899/202615744-fa8c3651-4472-4587-b127-ec8425949b76.png)

#### CDS View Associations

  Associationlarda aynı joinler gibi veriyi birleştirmemize yarar. Fakat bu kullanım performans dostu bir yaklaşım değildir.
  Bu performans sorunun üstesinden gelmek için associations kavramı geliştirildi. . Association'lar ile veriler yalnızca kullanıcı onu görmek istediğinde alınır, kullanıcı görmek istemiyorsa veriye erişim olmaz. Kullanılmayan tablolar varsa bu tablolardan veri çekilmez ve tabloya gidilmez. İki çeşit Association türü vardı. Bunlar Ad-Hoc ve Exposed Association olarak adlandırılır. Ad-Hoc Assocation normal Join gibi ikinci tablonun herhangi bir alanını kullanmak üzerine geliştirilen Assocation'lardır.
  
  1)Ad-Hoc Association
   
   4 Farklı kural ile kullanıyoruz. Bunlar cardinality ile gelen farklılıklardır. Cardinality association nın hangi join kısaca hangi kural ile veri çekeceğini söyler. [ .. ] görünümündedir.
    max değeri 0 min değeri ise * alamaz!
-[1..1]       inner join gibi çalışır
-[1] | [0..1] bulursa 1 tane bulamazsa getirmez
-[0..*]       left outer join gibi çalışır 0 veya tüm girişler
-[1..*]       left outer join gibi çalışır
  
  
  [1..*]*
![image](https://user-images.githubusercontent.com/76265899/202618344-9f601a9d-f030-49c1-b01a-4dff0ad9d8c0.png)

![image](https://user-images.githubusercontent.com/76265899/202618387-cedbae26-73b6-4236-9abb-8f467dfdeb8c.png)

![image](https://user-images.githubusercontent.com/76265899/202618582-ca9f6b7d-0606-4c52-a325-af53984c9cf6.png)


2) Exposed Association
   
   Exposed Association ise ilgili View için bir alan olarak görünmez ancak başka bir View aracılığıyla erişim sağlandığı zaman ya da abap programından direk olarak kullanılabilir.
   
  ![image](https://user-images.githubusercontent.com/76265899/202619066-c5d09030-58c2-4d76-92db-561a99ba9fd4.png)
  
  ![image](https://user-images.githubusercontent.com/76265899/202619133-27a42835-e617-4edb-b3bb-44c02b2549af.png)

Union & Union All
  2 farklı tablodaki alanları select çekmek istediğimizde kullanıyoruz. Fakat tablodan çekeceğimiz alanların aynı alanları olması zorunludur.
  Union sorgularında varsayılan mod Union Distinct'dir ve ikinci sorgudaki yinelenen kayıtları ortadan kaldırır.

  Union All da her iki tabloda ortak olan kayıtlar tolere edilmezler. Tekrar eden kayıtlar sorgu çıktısına dahil edilir. Veri duplicate çekilmiş olur.


#### Annotiation
    
    Ek açıklamalar anlamına gelen annotiation lar cds kullanımımızı zenginleştirir. Bunlar @ ile başlayıp yorum satırı gibi gözükse de cds view e özellikler katar.
    
    @AbapCatalog.compiler.compareFilter: true: Verileri filtreleme davranışını tanımlar, yani önce filtre koşullarını karşılaştırır ve eğer eşleşirlerse veriler getirilir. 
    Bunu 'false' olarak ayarlarsak 'KEY' kelimesini alanın önüne eklemenize bakılmaksızın, DB tablosu KEY alanları CDS View'ler için de KEY alanlar olarak tanımlanacaktır.
   
   @AbapCatalog.preserveKey: true: DB tablolarında tanımlanmış birden fazla KEY alan olabilir ve bu KEY alanların oluşturduğumuz CSD View'lerin KEY alanları olmasını isteyebiliriz.
   
   @AccessControl.authorizationCheck: #NOT_REQUIRED: CDS View'lere 'Güvenlik' parçası eklemek için kullanılır. 
   
   @EndUserText.label: ‘CDS View type #BASIC’:
CDS View'ler üzerindeki 'Açıklama' kısmının tayini için kullanılır.

    ABAP Annotations:

### AbapCatalog Annotations                     ### Component Annotations
    AccessControl Annotations                       Analytics Annotations
    ClientDependent Annotations                     AnalyticsDetails Annotations
    DataAging Annotations                           Consumption Annotations
    EndUserText Annotations                         Hierarchy Annotations
    Environment Annotations                         OData Annotations
                                                    Search Annotations
    



