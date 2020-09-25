---
title: Veri hizmeti kaynaklarına erişme (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, querying
- getting started, WCF Data Services
- querying the data service [WCF Data Service]
- WCF Data Services, getting started
- WCF Data Services, accessing data
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
ms.openlocfilehash: 02e45f4e67a80d3afb600f44ea9fa6a5e175310c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186685"
---
# <a name="accessing-data-service-resources-wcf-data-services"></a>Veri hizmeti kaynaklarına erişme (WCF Veri Hizmetleri)

WCF Veri Hizmetleri, verilerinizi URI 'Ler tarafından adreslenebilir kaynaklarla bir akış olarak göstermek için açık veri Protokolü 'Nü (OData) destekler. Bu kaynaklar [varlık veri modeli](../adonet/entity-data-model.md)varlık ilişkisi kurallarına göre temsil edilir. Bu modelde, varlıklar, bir uygulama etki alanında bulunan, müşteriler, siparişler, öğeler ve ürünler gibi veri türleri olan işletimsel birimleri temsil eder. Varlık verilerine, temsili durum aktarımı (REST) semantiği kullanılarak erişilir ve değiştirilir, özellikle Al, koy, POST ve DELETE için standart HTTP fiilleri.  
  
## <a name="addressing-resources"></a>Kaynakları adresleme  

 OData 'de, veri modeli tarafından sunulan tüm verileri bir URI kullanarak adresleyebilirsiniz. Örneğin, aşağıdaki URI, müşteri varlık türünün tüm örneklerinin girişlerini içeren Customers varlık kümesi olan bir akış döndürür:  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers>
  
 Varlıklarda varlık anahtarları adlı özel özellikler vardır. Varlık anahtarı, bir varlık kümesindeki tek bir varlığı benzersiz bir şekilde tanımlamak için kullanılır. Bu, varlık kümesindeki bir varlık türünün belirli bir örneğini ele almanıza olanak sağlar. Örneğin, aşağıdaki URI, anahtar değeri olan bir müşteri varlık türünün belirli bir örneği için bir giriş döndürür `ALFKI` :  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')>
  
 Bir varlık örneğinin ilkel ve karmaşık özellikleri de tek tek adreslenebilir. Örneğin, aşağıdaki URI `ContactName` belirli bir müşterinin özellik değerini içeren BIR XML öğesi döndürür:  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName>
  
 `$value`Uç noktasını ÖNCEKI URI 'ye dahil ettiğinizde, yanıt iletisinde yalnızca ilkel özelliğin değeri döndürülür. Aşağıdaki örnek, XML öğesi olmadan yalnızca "Maria Anders" dizesini döndürür:  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value>
  
 Varlıklar arasındaki ilişkiler veri modelinde ilişkilendirmelere göre tanımlanır. Bu ilişkilendirmeler bir varlık örneğinin gezinti özelliklerini kullanarak ilgili varlıkları adreslemeye olanak tanır. Bir gezinti özelliği, çoktan çoğa bir ilişki olması durumunda tek bir ilgili varlık ya da bire çok ilişki söz konusu olduğunda bir dizi ilgili varlık döndürebilir. Örneğin, aşağıdaki URI belirli bir müşteriyle ilgili tüm siparişlerin kümesi olan bir akış döndürür:  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders>
  
 Genellikle çift yönlü olan ilişkiler, bir dizi gezinti özelliği tarafından temsil edilir. Önceki örnekte gösterilen ilişkinin tersi olarak aşağıdaki URI, belirli bir sipariş varlığının ait olduğu müşteri varlığına yönelik bir başvuru döndürür:  
  
<https://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer>
  
 OData Ayrıca sorgu ifadelerinin sonuçlarına göre kaynakları adreslemenize de olanak sağlar. Bu, değerlendirilen bir ifadeye göre kaynak kümelerinin filtrelemesine olanak tanır. Örneğin, aşağıdaki URI kaynakları yalnızca, 22 Eylül 1997 tarihinden itibaren sevk edilen belirtilen müşteri için siparişleri döndürecek şekilde filtreliyor:  
  
`https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'`
  
 Daha fazla bilgi için bkz. [OData: URI kuralları](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).
  
## <a name="system-query-options"></a>Sistem sorgu seçenekleri  

 OData; filtreleme, sıralama ve sayfalama gibi kaynaklarda geleneksel sorgu işlemleri gerçekleştirmek için kullanabileceğiniz bir sistem sorgu seçenekleri kümesi tanımlar. Örneğin, aşağıdaki URI, tüm `Order` varlıkların kümesini, ilgili `Order_Detail` varlıkların yanı bir şekilde sona ermez posta kodlarını döndürür `100` :  
  
`https://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')&$expand=Order_Details&$orderby=ShipCity`
  
 Döndürülen akıştaki girişler, siparişlerin ShipCity özelliğinin değeri ile de sıralanır.  
  
 WCF Veri Hizmetleri, aşağıdaki OData sistem sorgu seçeneklerini destekler:  
  
|Sorgu seçeneği|Açıklama|  
|------------------|-----------------|  
|`$orderby`|Döndürülen akıştaki varlıklar için varsayılan bir sıralama düzeni tanımlar. Aşağıdaki sorgu, verilen müşteriler akışını ilçe ve şehre göre sıralar:<br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City>`|  
|`$top`|Döndürülen akışa eklenecek varlıkların sayısını belirtir. Aşağıdaki örnek ilk 10 müşteriyi atlar ve sonraki 10 ' u döndürür:<br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`|  
|`$skip`|Akıştaki varlıkları döndürmeye başlamadan önce atlanacak varlık sayısını belirtir. Aşağıdaki örnek ilk 10 müşteriyi atlar ve sonraki 10 ' u döndürür:<br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`|  
|`$filter`|Belirli ölçütlere göre akışta döndürülen varlıkları filtreleyen bir ifade tanımlar. Bu sorgu seçeneği, filtre ifadesini değerlendirmek için kullanılan bir mantıksal karşılaştırma işleçleri, aritmetik işleçler ve önceden tanımlanmış sorgu işlevleri kümesini destekler. Aşağıdaki örnek, 100 ' de bitolmayan posta kodlarının tüm siparişlerini döndürür:<br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')`|  
|`$expand`|Sorgu tarafından hangi ilgili varlıkların döndürüleceğini belirtir. İlgili varlıklar, sorgu tarafından döndürülen varlıkla birlikte bir akış veya bir giriş olarak yer alır. Aşağıdaki örnek, her bir siparişin öğe ayrıntılarıyla birlikte ' ALFKI ' müşterisi için sırayı döndürür:<br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details`|  
|`$select`|Varlığın özelliklerini tanımlayan projeksiyonun projeksiyonde döndürüleceğini belirtir. Varsayılan olarak, bir varlığın tüm özellikleri bir akışta döndürülür. Aşağıdaki sorgu varlığın yalnızca üç özelliğini döndürür `Customer` :<br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City`|  
|`$inlinecount`|Akışta döndürülen varlık sayısı sayısının akışa dahil edilmesini ister.|  
  
## <a name="addressing-relationships"></a>Adresleme Ilişkileri  

 OData, varlık kümelerinin ve varlık örneklerinin ele eklenmesine ek olarak, varlıklar arasındaki ilişkileri temsil eden ilişkilendirmeleri de sağlamanıza olanak sağlar. Bu işlevsellik, Northwind örnek veritabanındaki belirli bir siparişle ilişkili olan nakliyecinin gibi iki varlık örneği arasında bir ilişki oluşturabilmesinin veya değiştirebilmesi için gereklidir. OData `$link` , varlıklar arasındaki ilişkilendirmeleri özel olarak ele almak için bir işleci destekler. Örneğin, aşağıdaki URI, belirtilen sipariş için nakliyeci yeni bir nakliyeci değiştirmek üzere bir HTTP PUT isteği iletisinde belirtilmiştir.  
  
`https://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper`
  
 Daha fazla bilgi için bkz `3.2. Addressing Links between Entries` . [OData: URI kuralları](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).
  
## <a name="consuming-the-returned-feed"></a>Döndürülen akışı kullanma  

 OData kaynağının URI 'SI, hizmet tarafından sunulan varlık verilerini adreslemenize olanak sağlar. Bir Web tarayıcısının adres alanına bir URI girdiğinizde, istenen kaynağın OData akış temsili döndürülür. Daha fazla bilgi için [WCF veri hizmetleri hızlı başlangıç](quickstart-wcf-data-services.md)bölümüne bakın. Bir veri hizmeti kaynağının beklenen verileri döndürdüğü test için bir Web tarayıcısı yararlı olsa da, veri oluşturma, güncelleştirme ve silmeye yönelik üretim verileri Hizmetleri, genellikle bir Web sayfasındaki uygulama kodu veya komut dosyası dilleri tarafından erişilir. Daha fazla bilgi için bkz. [Istemci uygulamasında veri hizmeti kullanma](using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Protokolü Web sitesini aç](https://www.odata.org/)
