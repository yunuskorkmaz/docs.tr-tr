---
title: Veri Hizmeti kaynaklarına (WCF Veri Hizmetleri) erişme
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, querying
- getting started, WCF Data Services
- querying the data service [WCF Data Service]
- WCF Data Services, getting started
- WCF Data Services, accessing data
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
ms.openlocfilehash: d4f4de1fa12418bd56f9680e5414bfe7dd0aa128
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850224"
---
# <a name="accessing-data-service-resources-wcf-data-services"></a>Veri Hizmeti kaynaklarına (WCF Veri Hizmetleri) erişme
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] destekleyen [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] verilerinizi tarafından bir URI'leri adreslenebilir kaynaklarla bir akış olarak kullanıma sunmak için. Varlık ilişkisi kurallarına göre bu kaynakları temsil edilen [varlık veri modeli](../../../../docs/framework/data/adonet/entity-data-model.md). Bu modelde, işletimsel birimleri, müşteri, sipariş, öğeleri ve ürünleri gibi uygulama etki alanında veri türleri veri varlıkları temsil eder. Varlık verilerini erişilen ve özellikle standart HTTP fiilleri, GET, temsili durum aktarımı (REST) semantiği kullanarak değiştirilen koy Gönder ve Sil.  
  
## <a name="addressing-resources"></a>Kaynaklarını adreslemek  
 İçinde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], veri modeli tarafından bir URI aracılığıyla kullanıma sunulan herhangi bir veri adresi. Örneğin, aşağıdaki URI müşteri varlık türünün tüm örnekleri için girişler müşteriler varlık kümesi olan bir akış döndürür:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers  
```  
  
 Varlıklar, varlık anahtarları adlı özel özellik içerir. Varlık anahtarı bir varlık kümesindeki tek bir varlığı benzersiz olarak tanımlanabilmesi için kullanılır. Bu varlık kümesindeki bir varlık türünün belirli bir örneği ele almak sağlar. Örneğin, aşağıdaki URI'ın bir anahtar değere sahip müşteri varlık türünün belirli bir örneği için bir giriş döndürür `ALFKI`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')  
```  
  
 Bir varlık örneği basit ve karmaşık özelliklerini de ayrı ayrı çözülebilir. Örneğin, aşağıdaki URI içeren bir XML öğesi döndürür `ContactName` belirli bir müşteri için özellik değeri:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName  
```  
  
 Dahil ettiğinizde `$value` önceki urı'sindeki uç noktası, yalnızca basit özellik değerini yanıt iletisinde döndürülür. Aşağıdaki örnek XML öğesi olmadan yalnızca dize "Maria Anders" döndürür:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value  
```  
  
 Varlıklar arasında ilişkiler veri modelindeki ilişkileri tarafından tanımlanır. Bu ilişkilendirmeleri ilgili varlıkları bir varlık örneğini Gezinti özelliklerini kullanarak adres olanak sağlar. Bir gezinme özelliği ya da tek bir ilgili varlığı, söz konusu olduğunda çok bir ilişkinin veya bire çok ilişkisi söz konusu olduğunda, ilgili varlıkları kümesi döndürebilirsiniz. Örneğin, aşağıdaki URI, belirli bir müşteriye ilgili tüm siparişleri kümesi bir akış döndürür:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders  
```  
  
 Genellikle yönlü, ilişkiler, gezinti özellikleri çifti tarafından temsil edilir. Önceki örnekte gösterilen ilişkiyi ters olarak aşağıdaki URI belirli bir sırada varlığa ait olduğu müşteri varlığına yönelik bir başvuru döndürür:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer  
```  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Ayrıca, sorgu ifadeleri sonuçlarına göre kaynakları sağlar. Bu kaynakları üzerinde değerlendirilen bir ifade kümesi filtrelemek mümkün kılar. Örneğin, aşağıdaki URI, yalnızca 22 Eylül 1997'den beri gönderildi belirtilen müşterinin siparişlerini döndürmek için kaynakları filtreler:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'  
```  
  
 Daha fazla bilgi için [OData: URI kurallarına](https://go.microsoft.com/fwlink/?LinkId=185564).  
  
## <a name="system-query-options"></a>Sistem sorgu seçenekleri  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] filtreleme, sıralama ve disk belleği gibi kaynaklarda geleneksel sorgu işlemleri gerçekleştirmek için kullanabileceğiniz sistem sorgu seçenekleri kümesi tanımlar. Örneğin, aşağıdaki URI tüm kümesini döndürür; `Order` yanı sıra ilgili varlıkları `Order_Detail` varlıklar, posta kodlarının değil de sona `100`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')&$expand=Order_Details&$orderby=ShipCity  
```  
  
 Döndürülen akışa girdileri de siparişlerin ShipCity özelliğinin değeri sıralanır.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] şunları desteklemektedir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] sistem sorgu seçenekleri:  
  
|Sorgu seçeneği|Açıklama|  
|------------------|-----------------|  
|`$orderby`|Varlıklar için varsayılan sıralama döndürülen akışta tanımlar. Aşağıdaki sorgu akış İlçe ve city tarafından döndürülen müşterileri sıralar:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City`<br /><br /> Daha fazla bilgi için [OData: OrderBy sistem sorgusu seçeneği ($orderby)](https://go.microsoft.com/fwlink/?LinkId=186968).|  
|`$top`|Döndürülen akışta dahil etmek için varlık sayısını belirtir. Aşağıdaki örnekte ilk 10 müşteriler atlar ve sonraki 10 döndürür:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Daha fazla bilgi için [OData: üst sistem sorgusu seçeneği ($top)](https://go.microsoft.com/fwlink/?LinkId=186969).|  
|`$skip`|Akışta varlıkları döndürülecek başlatmadan önce atlamak için varlık sayısını belirtir. Aşağıdaki örnekte ilk 10 müşteriler atlar ve sonraki 10 döndürür:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> Daha fazla bilgi için [OData: atla sistem sorgusu seçeneği ($skip)](https://go.microsoft.com/fwlink/?LinkId=186971).|  
|`$filter`|Akışta varlıkları döndürülen filtreleri belirli bir ölçüte dayalı bir ifadeyi tanımlar. Bu sorgu seçeneği bir dizi mantıksal Karşılaştırma işleçleri, aritmetik işleçler ve filtre ifadesini değerlendirmek için kullanılan önceden tanımlanmış sorgu işlevleri destekler. Aşağıdaki örnek, posta kodları 100 bitmeyen tüm siparişleri döndürür:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')`<br /><br /> Daha fazla bilgi için [OData: Filtre sistem sorgusu seçeneği ($filter)](https://go.microsoft.com/fwlink/?LinkId=186972).|  
|`$expand`|Hangi ilgili varlıkları sorgu tarafından döndürülen belirtir. İlgili varlıklar bir akış veya giriş satır içi olarak sorgu tarafından döndürülen varlık ile dahil edilir. Aşağıdaki örnek, yanı sıra her bir order öğesi Ayrıntılar 'ALFKI' müşteri sipariş döndürür:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details`<br /><br /> Daha fazla bilgi için [OData: Sistem sorgusu ($expand) seçeneği genişletin](https://go.microsoft.com/fwlink/?LinkId=186973).|  
|`$select`|Entity öğesinin özellikleri tanımlayan bir yansıtma yansıtma döndürülür belirtir. Varsayılan olarak, bir akıştaki bir varlığın tüm özellikleri döndürülür. Aşağıdaki sorguda yalnızca üç özelliklerini döndürür `Customer` varlık:<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City`<br /><br /> Daha fazla bilgi için [OData: Sistem sorgusu seçeneği seçin ($select)](https://go.microsoft.com/fwlink/?LinkID=186076).|  
|`$inlinecount`|Akışta döndürülen varlık sayısını akış ile birlikte bir istek sayısı. Daha fazla bilgi için [OData: Inlinecount sistem sorgusu seçeneği ($inlinecount)](https://go.microsoft.com/fwlink/?LinkId=186975).|  
  
## <a name="addressing-relationships"></a>İlişkiler adresleme  
 Varlık kümeleri ve varlık örneklerinin yanı sıra [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] , varlıklar arasındaki ilişkileri gösteren ilişkilendirmeleri adres olanak tanır. Bu işlevleri oluşturmak veya değiştirmek gibi belirli bir sırada Northwind örnek veritabanıyla ilişkili shipper iki varlık örneği arasında bir ilişki için gereklidir. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] destekleyen bir `$link` varlıklar arasında ilişkilendirmeler özellikle yönelik işleci. Örneğin, aşağıdaki URI için yeni bir taşıyıcı shipper için belirtilen sırada değiştirmek için bir HTTP PUT İsteği iletisi belirtilir.  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper  
```  
  
 Daha fazla bilgi için [OData: girişler arasındaki bağlantılar adresleme](https://go.microsoft.com/fwlink/?LinkId=187351).  
  
## <a name="consuming-the-returned-feed"></a>Döndürülen akışa kullanma  
 URI'sini bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kaynak adresi varlık verileri hizmet tarafından sunulan, sağlar. Bir Web tarayıcısının Adres alanına bir URI girin, bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış istenen kaynağın gösterimini döndürülür. Daha fazla bilgi için [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Bir Web tarayıcısında test beklenen verileri bir veri hizmeti kaynağı döndürür, ayrıca oluşturmak, güncelleştirmek ve verileri silmek üretim Veri Hizmetleri genellikle uygulama kodu tarafından erişilen veya bir Web sayfasında dil komut dosyası için yararlı olabilir. Daha fazla bilgi için [bir istemci uygulamasında veri hizmeti kullanma](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Açık Veri Protokolü Web sitesi](https://go.microsoft.com/fwlink/?LinkID=182204)
