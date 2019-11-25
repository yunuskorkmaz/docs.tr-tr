---
title: WCF Veri Hizmetleri genel bakış
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: 21c09608bcf5d9f0b7bfc05b703d1ebe846a77bd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975065"
---
# <a name="wcf-data-services-overview"></a>WCF Veri Hizmetleri genel bakış
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], açık veri Protokolü (OData) kullanarak Web veya intranet için veri hizmetlerinin oluşturulmasını ve kullanımını mümkün bir şekilde sunar. OData, verilerinizi URI 'Ler tarafından adreslenebilir kaynaklar olarak kullanıma sunmanızı sağlar. Bu, özellikle Al, koy, POST ve DELETE için standart HTTP fiilleri olan temsili durum aktarımı (REST) semantiğini kullanarak verilere erişmenizi ve bunları değiştirmenize olanak sağlar. Bu konuda, hem OData tarafından tanımlanan desenler hem de uygulamalar ve ayrıca .NET Framework tabanlı uygulamalardaki OData 'ten yararlanmak için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] tarafından sağlanan tesislerin bir özeti verilmektedir.  
  
## <a name="address-data-as-resources"></a>Verileri kaynak olarak adres olarak  
 OData, verileri URI 'Ler tarafından adreslenebilir kaynaklar olarak kullanıma sunar. Kaynak yolları Varlık Veri Modeli varlık ilişkisi kurallarına göre oluşturulur. Bu modelde, varlıklar, bir uygulama etki alanındaki müşteri, sipariş, öğe ve ürün gibi işletimsel veri birimlerini temsil eder. Daha fazla bilgi için bkz. [varlık veri modeli](../adonet/entity-data-model.md).  
  
 OData ' de varlık kaynaklarını varlık türlerinin örneklerini içeren bir varlık kümesi olarak adreslerinolursunuz. Örneğin, URI <https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders>, `CustomerID` bir değeri olan müşteriyle ilişkili `Northwind` veri hizmetindeki tüm siparişleri döndürür `ALFKI.`  
  
 Sorgu ifadeleri, filtreleme, sıralama ve sayfalama gibi kaynaklara karşı geleneksel sorgu işlemleri gerçekleştirmenize olanak tanır. Örneğin, URI <https://services.odata.org/Northwind/Northwind.svc/Customers( ' ALFKI ')/Orders? $filter = Nakliye gt 50 >, kaynakları yalnızca $50 'den daha fazla nakliye maliyeti olan siparişleri döndürecek şekilde filtreler. Daha fazla bilgi için bkz. [veri hizmeti kaynaklarına erişme](accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Birlikte çalışabilen veri erişimi  
 OData, veri hizmetlerini .NET Framework kullanmayan uygulamalarla birlikte çalışabilir hale getirmek için standart Internet protokollerinde oluşturulur. Verileri adresleyerek standart URI 'Leri kullanabilmeniz için, uygulamanız temsili durum aktarımı (REST) semantiğini kullanarak verilere erişebilir ve değiştirebilir, özellikle Al, koy, POST ve DELETE için standart HTTP fiilleri. Bu, standart HTTP protokolleri üzerinden aktarılan verileri ayrıştırabilen ve bunlara erişebilen herhangi bir istemciden bu hizmetlere erişmenizi sağlar.  
  
 OData, Atom yayımlama Protokolü (AtomPub) için bir uzantılar kümesi tanımlar. Çeşitli istemci uygulamalarına ve platformlarına uyum sağlamak için birden fazla veri biçimindeki HTTP isteklerini ve yanıtlarını destekler. OData akışı, atom, JavaScript Nesne Gösterimi (JSON) ve düz XML olarak verileri temsil edebilir. Atom varsayılan biçim olsa da akışın biçimi HTTP isteğinin üst bilgisinde belirtilir. Daha fazla bilgi için bkz. [OData: Atom biçimi](https://go.microsoft.com/fwlink/?LinkID=185794) ve [OData: JSON biçimi](https://go.microsoft.com/fwlink/?LinkID=185795).  
  
 Verileri OData akışı olarak yayımlarken [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], önbelleğe alma ve kimlik doğrulama gibi diğer mevcut Internet tesislerini kullanır. Bunu gerçekleştirmek için, ASP.NET, Windows Communication Foundation (WCF) ve Internet Information Services (IIS) gibi mevcut barındırma uygulamaları ve hizmetleriyle tümleştirilir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
## <a name="storage-independence"></a>Depolama bağımsızlık  
 Kaynaklar bir varlık ilişkisi modeline göre değinse de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], temel alınan veri kaynağından bağımsız olarak OData akışlarını kullanıma sunar. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], URI tarafından tanımlanan bir kaynak için HTTP isteğini kabul ettikten sonra, istek seri durumdan çıkarılmış olur ve bu isteğin temsili bir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] sağlayıcısına geçirilir. Bu sağlayıcı, isteği veri kaynağına özgü biçime çevirir ve isteği temel alınan veri kaynağında yürütür. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], OData tarafından önceden belirlenmiş kaynaklara yönelik kavramsal modeli, temel alınan veri kaynağının belirli bir şemasından ayırarak depolama bağımsızlık kaynağına erişir.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], ilişkisel verileri kullanıma sunan veri Hizmetleri oluşturmanıza olanak tanımak için ADO.NET Entity Framework ile tümleşir. Varlık olarak adreslenebilir kaynakları içeren bir veri modeli oluşturmak için Varlık Veri Modeli araçlarını kullanabilirsiniz ve aynı zamanda bu model ile temel alınan veritabanındaki tablolar arasındaki eşlemeyi tanımlar. Daha fazla bilgi için bkz. [Entity Framework sağlayıcısı](entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Ayrıca, <xref:System.Linq.IQueryable%601> arabiriminin bir uygulamasını döndüren veri yapılarını sunan veri Hizmetleri oluşturmanıza olanak sağlar. Bu, .NET Framework türlerindeki verileri kullanıma sunan veri Hizmetleri oluşturmanıza olanak sağlar. Oluşturma, güncelleştirme ve silme işlemleri, <xref:System.Data.Services.IUpdatable> arabirimini de uyguladığınızda desteklenir. Daha fazla bilgi için bkz. [yansıma sağlayıcısı](reflection-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bu veri sağlayıcılarıyla nasıl tümleştirildiğini gösteren bir çizim için, bu konunun ilerleyen kısımlarında bulunan mimari diyagrama bakın.  
  
## <a name="custom-business-logic"></a>Özel Iş mantığı  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], hizmet işlemleri ve yakalayıcılar aracılığıyla bir veri hizmetine özel iş mantığı eklemenizi kolaylaştırır. Hizmet işlemleri, veri kaynaklarıyla aynı formda bulunan URI 'Ler tarafından adreslenebilir sunucuda tanımlanmış yöntemlerdir. Hizmet işlemleri bir işlemin döndürdüğü verileri filtrelemek, sıralamak ve sayfa verilerine yönelik sorgu ifadesi söz dizimini da kullanabilir. Örneğin, URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10`, `OrderDate`Londra 'dan müşteriler için siparişleri döndüren Northwind veri hizmeti üzerinde `GetOrdersByCity` adlı bir hizmet işleminin çağrısını temsil eder. Daha fazla bilgi için bkz. [hizmet işlemleri](service-operations-wcf-data-services.md).  
  
 Yakalayıcılar, bir veri hizmeti tarafından istek veya yanıt iletilerinin işlenmesinde tümleştirilecek özel uygulama mantığını etkinleştirir. Belirtilen varlık kümesinde bir sorgu, ekleme, güncelleştirme veya silme eylemi gerçekleştiğinde, bu dinleyici çağrılır. Daha sonra bir dinleyici, verileri değiştirebilir, yetkilendirme ilkesini uygulayabilir veya hatta işlemi sonlandırır. Bir veri hizmeti tarafından kullanıma sunulan belirli bir varlık kümesi için yakalayıcıyı yöntemleri açık olarak kaydedilmelidir. Daha fazla bilgi için bkz. [yakalayıcılar](interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>İstemci kitaplıkları  
 OData, veri hizmetleriyle etkileşim kurmak için bir Tekdüzen desenleri kümesi tanımlar. Bu, veri hizmetlerini kullanmayı kolaylaştıran istemci tarafı kitaplıkları gibi bu hizmetlere dayalı yeniden kullanılabilir bileşenler oluşturmaya yönelik bir fırsat sağlar.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] hem .NET Framework tabanlı hem de Silverlight tabanlı istemci uygulamaları için istemci kitaplıkları içerir. Bu istemci kitaplıkları .NET Framework nesneleri kullanarak veri hizmetleriyle etkileşim kurmanızı sağlar. Bunlar ayrıca nesne tabanlı sorguları ve LINQ sorgularını, ilgili nesneleri, değişiklik izlemeyi ve kimlik çözümlemesini destekler. Daha fazla bilgi için [WCF veri Hizmetleri Istemci kitaplığı](wcf-data-services-client-library.md)' na bakın.  
  
 .NET Framework ve Silverlight ile birlikte bulunan OData istemci kitaplıklarına ek olarak, PHP, AJAX ve Java uygulamaları gibi istemci uygulamalarında bir OData akışını kullanmanıza olanak tanıyan başka istemci kitaplıkları da vardır. Daha fazla bilgi için bkz. [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="architecture-overview"></a>Mimariye Genel Bakış  
 Aşağıdaki diyagramda OData akışlarını gösterme ve OData özellikli istemci kitaplıklarında bu akışları kullanma [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] mimarisi gösterilmektedir:  
  
 ![WCF Veri Hizmetleri mimari diyagramını gösteren ekran görüntüsü.](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri 4.5](index.md)
- [Başlarken](getting-started-with-wcf-data-services.md)
- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [Veri hizmeti kaynaklarına erişme (WCF Veri Hizmetleri)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Temsili durum aktarımı (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
