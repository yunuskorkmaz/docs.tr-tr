---
title: WCF veri hizmetleri genel bakış
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: eb9adf5ff66a8b45bea79a9abaa139a46abb5b39
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56094028"
---
# <a name="wcf-data-services-overview"></a>WCF veri hizmetleri genel bakış
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kullanarak oluşturma ve veri hizmetlerinin Web veya intranet tüketim sağlayan [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Verilerinizi tarafından bir URI'leri adreslenebilir kaynakları olarak kullanıma sunmanıza olanak sağlar. Bu, erişmenize olanak tanır ve özellikle standart HTTP fiilleri, temsili durum aktarımı (REST) semantiği kullanarak, değişiklik verilerini al koy, Gönder ve Sil. Bu konu desenler ve uygulamalar tarafından tanımlanan genel bir bakış sağlar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ve ayrıca tarafından sağlanan özellikleri [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] yararlanmak için [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] .NET Framework tabanlı uygulamalarda.  
  
## <a name="address-data-as-resources"></a>Adres veri kaynakları olarak  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] verileri tarafından bir URI'leri adreslenebilir kaynakları olarak kullanıma sunar. Kaynak yolları, varlık veri modeli varlık ilişkisi kurallarına dayalı oluşturulur. Bu modelde, işletimsel birimleri, müşteri, sipariş, öğeleri ve ürünleri gibi uygulama etki alanında veri varlıkları temsil eder. Daha fazla bilgi için [varlık veri modeli](../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 İçinde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], varlık türleri örneklerini içeren bir varlık kümesi varlık kaynak adresi. Örneğin, URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` tüm siparişleri döndürür `Northwind` müşteriyle ilgili veri hizmeti bir `CustomerID` değeri `ALFKI.`  
  
 Sorgu ifadeleri filtreleme, sıralama ve disk belleği gibi kaynaklarda geleneksel sorgu işlemleri gerçekleştirmenize olanak sağlar. Örneğin, URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` kaynakları yalnızca bir navlun maliyeti $50'den fazla siparişleri döndürmek için filtre uygular. Daha fazla bilgi için [veri hizmeti kaynaklarına erişme](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Birlikte çalışabilen veri erişimi  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Veri Hizmetleri .NET Framework kullanmayan uygulamalar ile birlikte çalışabilir yapmak için standart Internet protokolleri üzerinde oluşturur. Standart bir URI'leri adresi verilere kullanabileceğinizden, uygulamalarınıza erişmek ve özellikle standart HTTP fiilleri, temsili durum aktarımı (REST) semantiği kullanarak, değişiklik verilerini al koy, Gönder ve Sil. Bu hizmetlerin herhangi bir ayrıştırabilen istemci ve standart HTTP protokolleri üzerinden aktarılan verilere erişmenizi sağlar.  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Atom yayımlama Protokolü (AtomPub) uzantıları kümesi tanımlar. Bu seçenek, HTTP isteklerini ve yanıtlarını çeşitli istemci uygulamaları ve platformlara uyum sağlamak için birden fazla veri biçimi destekler. Bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış veri Atom, JavaScript nesne gösterimi (JSON) ve düz XML olarak temsil edebilir. Atom varsayılan biçimi olsa da, HTTP istek üst bilgisinde akış biçimi belirtildi. Daha fazla bilgi için [OData: Atom biçimi](https://go.microsoft.com/fwlink/?LinkID=185794) ve [OData: JSON biçiminde](https://go.microsoft.com/fwlink/?LinkID=185795).  
  
 Veri yayımlama sırasında bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışına [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] diğer var olan Internet özellikleri önbelleğe alma ve kimlik doğrulama gibi işlemleri için kullanır. Bunu gerçekleştirmek için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] mevcut barındırma uygulamaları ve ASP.NET, Windows Communication Foundation (WCF) ve Internet Information Services (IIS) gibi hizmetler ile tümleştirilir.  
  
## <a name="storage-independence"></a>Depolama bağımsızlığı  
 Bir varlık ilişkisi modelini temel alan kaynaklara yönelik olsa da [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kullanıma [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları temel alınan veri kaynağı ne olursa olsun. Sonra [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir URI tanımlar, istek seri durumdan ve bir gösterimiyse, bu istek için geçirilen bir kaynak için bir HTTP isteği kabul eden bir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] sağlayıcısı. Bu sağlayıcı, istek bir veri kaynağına özgü biçimine çevirir ve temel alınan veri kaynağında isteği yürütür. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kaynaklar tarafından belirlenen ele kavramsal model ayrılarak depolama bağımsızlığı elde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] temel alınan veri kaynağının belirli şemadan.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İlişkisel verileri açığa veri hizmetleri oluşturmanıza olanak sağlayan için ADO.NET Entity Framework ile tümleştirilir. Varlık veri modeli araçları varlıklar olarak adreslenebilir kaynakları içeren bir veri modeli oluşturabilir ve aynı zamanda bu modeli ve tablolar arasındaki eşleme temel alınan veritabanında tanımlamak için kullanabilirsiniz. Daha fazla bilgi için [Entity Framework sağlayıcısı](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Ayrıca uygulaması döndüren tüm veri yapılarını kullanıma Veri Hizmetleri oluşturmanızı sağlayan <xref:System.Linq.IQueryable%601> arabirimi. Bu, .NET Framework türleri verileri ortaya çıkaran veri hizmetleri oluşturmanıza olanak sağlar. Oluşturma, güncelleştirme ve silme işlemleri de uygularken desteklenir <xref:System.Data.Services.IUpdatable> arabirimi. Daha fazla bilgi için [yansıma sağlayıcısı](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).  
  
 Nasıl bir gösterimi için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] tümleşir bu veri sağlayıcılarıyla mimari diyagramı bu konunun ilerleyen bölümlerinde bkz.  
  
## <a name="custom-business-logic"></a>Özel iş mantığı  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir veri hizmeti hizmet işlemleri ve dinleyicileri aracılığıyla özel iş mantığı eklemek kolaylaştırır. Hizmet işlemleri tarafından bir URI'leri adreslenebilir veri kaynakları ile aynı formda sunucuda tanımlanmış yöntemlerdir. Hizmet işlemleri, filtre, sıralama ve bir işlem tarafından döndürülen sayfası verileri için sorgu ifadesi söz dizimi de kullanabilirsiniz. Örneğin, URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` bir çağrı adlı bir hizmet işlemi temsil eden `GetOrdersByCity` müşteriler için siparişleri Londra'dan döndürür Northwind verileri hizmeti üzerinde disk belleğine göre sıralanmış sonuçları ile `OrderDate`. Daha fazla bilgi için [hizmet işlemleri](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Kesiciler, özel uygulama mantığını istek veya yanıt iletilerinin işlenmesini içinde bir veri hizmeti tarafından tümleştirilecek şekilde etkinleştirin. Dinleyicileri bir sorgu, ekleme, güncelleştirme veya silme eylemi, belirtilen varlık kümesi üzerinde oluştuğunda çağrılır. Bir dinleyiciyi sonra veri alter, yetkilendirme ilkesini zorlama veya bile işlemi sonlandırın. Veri Hizmeti tarafından sunulan belirtilen varlık kümesi için dinleyiciyi yöntemleri açıkça kayıtlı olması gerekir. Daha fazla bilgi için [dinleyicileri](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>İstemci kitaplıkları  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Veri Hizmetleri ile etkileşim kurmak için Tekdüzen desenleri tanımlar. Bu, veri hizmetlerinin kullanımını kolaylaştıran istemci tarafı kitaplıkları gibi hizmetlerin temel alan yeniden kullanılabilir bileşenler oluşturmak için bir fırsat sağlar.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] hem .NET Framework ve Silverlight tabanlı istemci uygulamaları için istemci kitaplıkları içerir. Bu istemci kitaplıkları, .NET Framework nesnelerini kullanarak veri Hizmetleri ile etkileşim kurmak etkinleştirin. Ayrıca nesne tabanlı sorgular destekledikleri ve LINQ sorguları ilgili nesneler yükleniyor, izleme ve kimlik çözümlemesi değiştirin. Daha fazla bilgi için [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
 Ek olarak [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] istemci kitaplıkları, .NET Framework ve Silverlight, dahil edilen kullanmasına olanak sağlayan diğer istemci kitaplıkları vardır bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] , PHP, AJAX ve Java uygulamaları gibi istemci uygulamaları içindeki akış. Daha fazla bilgi için [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="architecture-overview"></a>Mimariye Genel Bakış  
 Aşağıdaki diyagramda gösterilmektedir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] gösterme mimari [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları ve bu akışları kullanarak [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-etkin istemci kitaplıkları:  
  
 ![WCF Veri Hizmetleri mimarisi diyagramı](../../../../docs/framework/data/wcf/media/astoriaservicearch.gif "AstoriaServiceArch")  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WCF Veri Hizmetleri 4.5](../../../../docs/framework/data/wcf/index.md)
- [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Veri Hizmeti kaynaklarına (WCF Veri Hizmetleri) erişme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Temsili durum aktarımı (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
