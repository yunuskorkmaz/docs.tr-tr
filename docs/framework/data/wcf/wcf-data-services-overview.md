---
title: "WCF veri hizmetleri genel bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c98ecc987f4710d344f6eab07563a14cbf4d9962
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-data-services-overview"></a>WCF veri hizmetleri genel bakış
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]kullanarak oluşturma ve Veri Hizmetleri Web veya intranet tüketimini sağlayan [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Verilerinizi URI tarafından adreslenebilir kaynaklar olarak kullanıma sunmak etkinleştirir. Bu, erişmenize olanak tanır ve temsili durum aktarımı (REST), özellikle de, standart HTTP fiilleri semantiği kullanarak değişiklik verilerini al koy, POST ve SİLİN. Bu konu desenleri ve uygulamalar tarafından tanımlanan bir bakış sunar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ve ayrıca tarafından sağlanan özellikleri [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] yararlanmak için [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] .NET Framework tabanlı uygulamalarda.  
  
## <a name="address-data-as-resources"></a>Adres veri kaynakları olarak  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Veri URI tarafından adreslenebilir kaynakları olarak kullanıma sunar. Kaynak yolları, varlık veri modeli varlık ilişkisi kurallarına göre oluşturulur. Bu modelde, müşteriler, siparişler, öğeleri ve ürünler gibi bir uygulama etki alanındaki verilerin işletimsel birimleri varlık temsil eder. Daha fazla bilgi için bkz: [varlık veri modeli](../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 İçinde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], varlık türleri örneklerini içeren bir varlık kümesi varlık kaynakları adres. Örneğin, URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` tüm siparişleri döndürür `Northwind` müşteriyle ilişkili veri hizmeti bir `CustomerID` değeri`ALFKI.`  
  
 Sorgu ifadeleri filtreleme, sıralama ve disk belleği gibi kaynaklara karşı geleneksel sorgu işlemleri gerçekleştirmek etkinleştirin. Örneğin, URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` yalnızca $50'den fazla nakliye maliyetini taşıyan siparişler döndürülecek kaynakların filtreler. Daha fazla bilgi için bkz: [veri hizmeti kaynaklar erişim](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Birlikte çalışabilir veri erişimi  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Veri Hizmetleri .NET Framework kullanmayan uygulamalar birlikte çalışabilir yapmak için standart Internet protokolleri inşa edilmiştir. Standart URI adresi verilere kullanabileceğinizden, uygulamanızın erişebilir ve temsili durum aktarımı (REST), özellikle de, standart HTTP fiilleri semantiği kullanarak değişiklik verilerini al koy, POST ve SİLİN. Bu, bu hizmetleri ayrıştıramıyor istemci ve standart HTTP protokoller üzerinden aktarılan erişim verilerini erişmenize olanak tanır.  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Atom yayımlama Protokolü (AtomPub) uzantıları kümesini tanımlar. Bu seçenek, HTTP isteklerini ve yanıtlarını çeşitli istemci uygulamaları ve platformlar uyum sağlamak için birden fazla veri biçiminde destekler. Bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış veri Atom, JavaScript nesne gösterimi (JSON) ve düz XML olarak temsil eder. Atom varsayılan biçimi olsa da, akış biçimlerinin HTTP istek üstbilgisinde belirtilir. Daha fazla bilgi için bkz: [OData: Atom biçimi](http://go.microsoft.com/fwlink/?LinkID=185794) ve [OData: JSON biçimine](http://go.microsoft.com/fwlink/?LinkID=185795).  
  
 Veri olarak yayımlarken bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] önbelleğe alma ve kimlik doğrulama gibi işlemleri için varolan diğer Internet tesis kullanır. Bunu başarmak için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] barındırma uygulamalarınız ve ASP.NET, Windows Communication Foundation (WCF) ve Internet Information Services (IIS) gibi hizmetleri ile tümleşir.  
  
## <a name="storage-independence"></a>Depolama bağımsızlığı  
 Bir varlık ilişkisi modelini temel alan kaynakları ele rağmen [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kullanıma [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları veri kaynağındaki bağımsız olarak. Sonra [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] tanımlayan bir URI, istek serisi ve bu isteği bir gösterimini geçirilir bir kaynak için bir HTTP istek kabul eden bir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] sağlayıcısı. Bu sağlayıcı isteği bir veri kaynağı özgü biçimine dönüştürür ve temel alınan veri kaynağında isteği yürütür. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]tarafından belirlenen kaynakları adresleri kavramsal model ayırarak depolama bağımsızlığı başarır [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] veri kaynağındaki belirli şemasından.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]İlişkisel veri kullanıma veri hizmetleri oluşturmanıza olanak sağlaması için ADO.NET Entity Framework ile tümleşir. Varlık veri modeli araçları varlıklar olarak adreslenebilir kaynakları içeren bir veri modeli oluşturmak ve aynı anda bu modeli ve tablolar arasında eşleme temel veritabanında tanımlamak için kullanabilirsiniz. Daha fazla bilgi için bkz: [Entity Framework sağlayıcısı](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]uygulaması dönüş hiçbir veri yapılarını kullanıma Veri Hizmetleri oluşturmanızı sağlayan <xref:System.Linq.IQueryable%601> arabirimi. Bu, .NET Framework türünden verileri kullanıma veri hizmetleri oluşturmanıza olanak sağlar. Oluşturma, güncelleştirme ve silme işlemleri de uyguladığınızda desteklenir <xref:System.Data.Services.IUpdatable> arabirimi. Daha fazla bilgi için bkz: [yansıma sağlayıcısı](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).  
  
 Nasıl bir çizimi için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] tümleştirir bu veri sağlayıcılarıyla mimari diyagramı bu konunun ilerleyen bölümlerinde bkz.  
  
## <a name="custom-business-logic"></a>Özel iş mantığı  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Veri Hizmeti hizmet işlemleri ve dinleyiciler aracılığıyla özel iş mantığı eklemek kolaylaştırır. Hizmet, URI tarafından adreslenebilir veri kaynakları aynı formunda sunucuda tanımlanan yöntemler işlemleridir. Hizmet işlemleri sorgu ifade sözdizimi bir işlem tarafından döndürülen sayfa verileri filtreleme, sipariş ve için de kullanabilirsiniz. Örneğin, URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` adlı bir hizmet işlemi için bir çağrı temsil eden `GetOrdersByCity` Londra'dan müşterilerin siparişleri döndürür Northwind veri hizmeti üzerinde ile göre sıralanmış sonuçları disk belleğine alınan `OrderDate`. Daha fazla bilgi için bkz: [hizmet işlemleri](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Dinleyiciler özel uygulama mantığını istek veya yanıt iletilerinin işlenmesini de bir veri hizmeti tarafından tümleştirilecek şekilde etkinleştirin. Sorgu, ekleme, güncelleştirme veya silme eylemi belirtilen varlık kümesinde oluştuğunda dinleyiciler denir. Bir dinleyiciden sonra veri alter, yetkilendirme ilkesini zorlama veya bile işlemini sonlandırır. Bir veri hizmeti tarafından sunulan bir belirtilen varlık kümesi için dinleyiciyi yöntemleri açıkça kayıtlı olması gerekir. Daha fazla bilgi için bkz: [dinleyiciler](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>İstemci kitaplıkları  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Veri Hizmetleri ile etkileşim için Tekdüzen desenleri kümesini tanımlar. Bu, daha kolay veri hizmetleri kullanmak için istemci tarafı kitaplıklar gibi hizmetlerin temel alan yeniden kullanılabilir bileşenler oluşturma olanağı sağlar.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]hem .NET Framework ve Silverlight tabanlı istemci uygulamaları için istemci kitaplıklarını içerir. Bu istemci kitaplıkları, .NET Framework nesneleri kullanarak veri Hizmetleri ile etkileşim kurmasına olanak tanır. Bunlar ayrıca nesne tabanlı sorgularını destekler ve ilişkili nesneleri yüklenirken LINQ sorgularını izleme ve kimlik çözümü değiştirin. Daha fazla bilgi için bkz: [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
 Ek olarak [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] istemci kitaplıkları, Silverlight, .NET Framework ile dahil kullanmasına olanak tanıyan diğer istemci kitaplığı bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] PHP, AJAX ve Java uygulamaları gibi istemci uygulamalarını akış. Daha fazla bilgi için bkz: [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="architecture-overview"></a>Mimarisine genel bakış  
 Aşağıdaki diyagramda gösterilmektedir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] gösterme mimari [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları ve bu akışlarında kullanarak [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-istemci kitaplıkları etkin:  
  
 ![WCF Veri Hizmetleri mimarisi diyagramı](../../../../docs/framework/data/wcf/media/astoriaservicearch.gif "AstoriaServiceArch")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri 4.5](../../../../docs/framework/data/wcf/index.md)  
 [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Veri Hizmeti (WCF Veri Hizmetleri) erişme](http://msdn.microsoft.com/en-us/1e54a2b9-2ec6-4002-b8f8-c1d8df37c350)  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Temsili durum aktarımı (REST)](http://go.microsoft.com/fwlink/?LinkId=113919)
