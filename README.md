# CDS(Core Data Services) View

Cds, Sap hana nın sağladığı değişimlerden, avantajlardan biridir.
Cds, veri modellerinin uygulama düzeyi yerine veri tabanı düzeyinde kullanılmasını ve tanımlanmasını sağlayarak performansı artırmayı amaçlar.

Veri modelleri, veri tanımlama dili [DDL] ve veri kontrol dili[DCL] ne dayalıdır.

Hananın en önemli getirisi veri işleme açısından, işlemeyi daha hızlı hale getirmek için veri tabanına direk erişim sağlaması ve ağ sebebiyle gelişebilecek gecikmeleri ortadan kaldırmasıdır.
Yoğun veri içeren işlemler  code to data paradigmasını kullanarak veri tabanı katmanının kendisinde gerçekleştirilir. Bu kodun işlenmek üzere aşağıya itilmesi anlamına gelir yani code push down denilmektedir. Böyle isimlendirmesinin sebebi ise, veriye ulaşma ve onu hazır etme işlemlerini uygulama sunucusu üzerinde yapmaktansa, veri tabanı seviyesine indirgemesi ve yükü veri tabanına vermesidir. 

![image](https://user-images.githubusercontent.com/76265899/202611456-918e2cfb-6d46-47f6-8cea-a6b3fdd3b939.png)

