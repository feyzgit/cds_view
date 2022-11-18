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





