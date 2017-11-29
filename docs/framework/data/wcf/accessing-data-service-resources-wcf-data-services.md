---
title: "Erişen veri hizmeti kaynakları (WCF Veri Hizmetleri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, querying
- getting started, WCF Data Services
- querying the data service [WCF Data Service]
- WCF Data Services, getting started
- WCF Data Services, accessing data
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 569830c5fbb9ecb837482202a4eb5a096ce21962
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-data-service-resources-wcf-data-services"></a>Erişen veri hizmeti kaynakları (WCF Veri Hizmetleri)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]destekleyen [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] verilerinizi URI tarafından adreslenebilir kaynaklarla akışı olarak kullanıma sunmak için. Bu kaynaklar varlık ilişkisi kurallarına göre temsil [varlık veri modeli](../../../../docs/framework/data/adonet/entity-data-model.md). Bu modelde, varlık veri türleridir müşteriler, siparişler, öğeleri ve ürünler gibi bir uygulama etki alanındaki verilerin işletimsel birimleri temsil eder. Varlık veri erişilen ve temsili durum aktarımı (REST), özellikle de, GET, standart HTTP fiilleri semantiği kullanarak değiştirilen, PUT, POST ve SİLİN.  
  
## <a name="addressing-resources"></a>Kaynakları adresleme  
 İçinde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], bir URI'yı kullanarak veri modeli tarafından kullanıma sunulan herhangi bir veri adres. Örneğin, aşağıdaki URI müşteri varlık türünün tüm örneklerini girişleri içerir müşteriler varlık kümesi bir akış döndürür:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers  
```  
  
 Varlıklar, varlık anahtarları adlı özel özellik sahiptir. Bir varlık anahtarı, bir varlık kümesindeki tek bir varlık benzersiz şekilde tanımlamak için kullanılır. Bu, bir varlık türünün varlık kümesindeki belirli bir örneğine yönelik olarak sağlar. Örneğin, aşağıdaki URI anahtar değerine sahip müşteri varlık türü belirli bir örneği için bir giriş döndürür `ALFKI`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')  
```  
  
 Bir varlık örneği basit ve karmaşık özelliklerini de ayrı ayrı çözülebilir. Örneğin, aşağıdaki URI içeren bir XML öğesi döndürür `ContactName` belirli bir müşteri için özellik değeri:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName  
```  
  
 Dahil ettiğinizde `$value` endpoint önceki URI, yalnızca bir ilkel özellik değeri yanıt iletisinde döndürülür. Aşağıdaki örnek XML öğesi olmadan yalnızca dize "Maria Anders" döndürür:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value  
```  
  
 Varlıklar arasındaki ilişkiler veri modelinde ilişkilendirmeleri tarafından tanımlanır. Bu ilişkileri bir varlık örneğinin Gezinti özellikleri kullanarak ilgili varlıklar adres olanak sağlar. Bir gezinti özelliği ya da tek bir ilişkili varlık, bir çok-bir ilişkisi veya bir-çok ilişkisi söz konusu olduğunda ilgili varlık kümesi durumunda geri dönebilirsiniz. Örneğin, aşağıdaki URI belirli bir müşteriye ilişkili tüm siparişler kümesidir bir akış döndürür:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders  
```  
  
 Çift yönlü genellikle, ilişkileri Gezinti özellikleri çifti ile temsil edilir. Önceki örnekte gösterilen ilişki geriye doğru, aşağıdaki URI belirli bir sırada varlık ait olduğu müşteri varlığa bir başvuru döndürür:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer  
```  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Ayrıca, sorgu ifadeleri sonuçlarına dayalı adresi kaynakları sağlar. Bu ayarlar üzerinde hesaplanan bir ifade tabanlı kaynakların filtrelemek mümkün kılar. Örneğin, aşağıdaki URI yalnızca 22 Eylül 1997 beri gönderilen siparişler belirtilen müşteri için döndürülecek kaynakların filtreler:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'  
```  
  
 Daha fazla bilgi için bkz: [OData: URI kuralları](http://go.microsoft.com/fwlink/?LinkId=185564).  
  
## <a name="system-query-options"></a>Sistem sorgu seçenekleri  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]filtreleme, sıralama ve disk belleği gibi kaynaklara karşı geleneksel sorgu işlemleri gerçekleştirmek için kullanabileceğiniz sistem sorgu seçenekleri kümesini tanımlar. Örneğin, aşağıdaki URI tüm kümesini döndürür; `Order` ilgili birlikte varlıklar `Order_Detail` posta kodlarının bitemez, varlıklar, `100`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')&$expand=Order_Details&$orderby=ShipCity  
```  
  
 Döndürülen akışa girdileri de siparişleri Sevk Şehri özelliğinin değeri olarak sıralanır.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Aşağıdaki destekleyen [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] sistem sorgu seçenekleri:  
  
|Sorgu seçeneği|Açıklama|  
|------------------|-----------------|  
|`$orderby`|Varlıklar için varsayılan bir sıralama düzeni döndürülen akışta tanımlar. Aşağıdaki sorgu akış İlçe ve şehir tarafından döndürülen müşteriler siparişleri:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City`<br /><br /> Daha fazla bilgi için bkz: [OData: OrderBy sistem sorgusu seçeneği ($orderby)](http://go.microsoft.com/fwlink/?LinkId=186968).|  
|`$top`|Döndürülen akışta içerecek şekilde varlıkların sayısını belirtir. Aşağıdaki örnek ilk 10 müşteriler atlar ve sonraki 10 döndürür:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Daha fazla bilgi için bkz: [OData: üst sistem sorgusu seçeneği ($top)](http://go.microsoft.com/fwlink/?LinkId=186969).|  
|`$skip`|Akışta varlıkları döndürme başlatmadan önce atlamak için varlık sayısını belirtir. Aşağıdaki örnek ilk 10 müşteriler atlar ve sonraki 10 döndürür:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Daha fazla bilgi için bkz: [OData: atla sistem sorgusu seçeneği ($skip)](http://go.microsoft.com/fwlink/?LinkId=186971).|  
|`$filter`|Akışta varlıkları döndürülen filtreleri belirli bir ölçüte dayalı bir ifadeyi tanımlar. Bu sorgu seçeneği bir dizi mantıksal Karşılaştırma işleçleri, aritmetik işleçler ve filtre ifadesi değerlendirmek için kullanılan önceden tanımlanmış sorgu işlevleri destekler. Aşağıdaki örnek, posta kodlarının 100 bitmeyen tüm siparişleri döndürür:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')`<br /><br /> Daha fazla bilgi için bkz: [OData: Filtre sistem sorgusu seçeneği ($filter)](http://go.microsoft.com/fwlink/?LinkId=186972).|  
|`$expand`|Hangi ilgili varlıkların sorgu tarafından döndürülen belirtir. İlgili varlıklar bir akış veya giriş satır içi olarak sorgu tarafından döndürülen varlığı ile dahil edilir. Aşağıdaki örnek, öğe ayrıntıları her sipariş için birlikte 'ALFKI' müşteri siparişi döndürür:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details`<br /><br /> Daha fazla bilgi için bkz: [OData: Sistem sorgulama ($expand) seçeneğini genişletin](http://go.microsoft.com/fwlink/?LinkId=186973).|  
|`$select`|Varlık özelliklerini tanımlayan bir yansıtma, yansıtma döndürülür belirtir. Varsayılan olarak, bir varlığın tüm özellikleri akış döndürülür. Aşağıdaki sorguda yalnızca üç özelliklerini döndürür `Customer` varlık:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City`<br /><br /> Daha fazla bilgi için bkz: [OData: Sistem sorgusu seçeneği ($select)](http://go.microsoft.com/fwlink/?LinkID=186076).|  
|`$inlinecount`|Akışta döndürülen varlıkları sayısını akış ile birlikte bir istek sayısı. Daha fazla bilgi için bkz: [OData: Inlinecount sistem sorgusu seçeneği ($inlinecount)](http://go.microsoft.com/fwlink/?LinkId=186975).|  
  
## <a name="addressing-relationships"></a>İlişkileri adresleme  
 Varlık kümeleri ve varlık örneklerini adresleme yanı sıra [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] varlıklar arasındaki ilişkiler temsil ilişkilendirmeleri adres olanak tanır. Bu işlev oluşturma veya değiştirme Northwind örnek veritabanı belirli bir sırada ilgili taşıyıcı gibi iki varlık örnekleri arasında bir ilişki kurabilmesi için gereklidir. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]destekleyen bir `$link` özellikle varlıklar arasında ilişkilendirmeler adres işleci. Örneğin, aşağıdaki URI için yeni bir taşıyıcı belirtilen sırayla taşıyıcı değiştirmek için bir HTTP PUT İsteği iletisi belirtildi.  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper  
```  
  
 Daha fazla bilgi için bkz: [OData: girişleri arasındaki bağlantıları adresleme](http://go.microsoft.com/fwlink/?LinkId=187351).  
  
## <a name="consuming-the-returned-feed"></a>Döndürülen akışa kullanma  
 URI'sini bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kaynak adresi varlık veri hizmeti tarafından kullanıma sunulan, sağlar. Bir Web tarayıcısının Adres alanına bir URI girdiğinizde bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] istenen kaynak akış gösterimini döndürülür. Daha fazla bilgi için bkz: [WCF Veri Hizmetleri Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Bir Web tarayıcısı test beklenen verileri bir veri hizmeti kaynak döndürür, da oluşturmak, güncelleştirmek ve verileri silme üretim Veri Hizmetleri genellikle uygulama kodu tarafından erişilen veya bir Web sayfasında dil komut dosyası için yararlı olabilir. Daha fazla bilgi için bkz: [veri hizmeti istemci uygulamasında kullanma](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Açık Veri Protokolü Web sitesi](http://go.microsoft.com/fwlink/?LinkID=182204)
