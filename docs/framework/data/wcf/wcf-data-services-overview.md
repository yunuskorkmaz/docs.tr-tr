---
title: WCF Veri Hizmetleri genel bakış
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: a4121bb10de7bfe51c5fec6bc14a40ad4bdcdaf7
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900887"
---
# <a name="wcf-data-services-overview"></a>WCF Veri Hizmetleri genel bakış
WCF Veri Hizmetleri, açık veri Protokolü (OData) kullanarak Web veya intranet için veri hizmetlerinin oluşturulmasını ve kullanımını mümkün bir şekilde sunar. OData, verilerinizi URI 'Ler tarafından adreslenebilir kaynaklar olarak kullanıma sunmanızı sağlar. Bu, özellikle Al, koy, POST ve DELETE için standart HTTP fiilleri olan temsili durum aktarımı (REST) semantiğini kullanarak verilere erişmenizi ve bunları değiştirmenize olanak sağlar. Bu konuda, hem OData tarafından tanımlanan desenler hem de uygulamalar ve ayrıca .NET Framework tabanlı uygulamalardaki OData 'ten yararlanmak için WCF Veri Hizmetleri tarafından sağlanan tesislerin bir özeti verilmektedir.  
  
## <a name="address-data-as-resources"></a>Verileri kaynak olarak adres olarak  
 OData, verileri URI 'Ler tarafından adreslenebilir kaynaklar olarak kullanıma sunar. Kaynak yolları Varlık Veri Modeli varlık ilişkisi kurallarına göre oluşturulur. Bu modelde, varlıklar, bir uygulama etki alanındaki müşteri, sipariş, öğe ve ürün gibi işletimsel veri birimlerini temsil eder. Daha fazla bilgi için bkz. [varlık veri modeli](../adonet/entity-data-model.md).  
  
 OData ' de varlık kaynaklarını varlık türlerinin örneklerini içeren bir varlık kümesi olarak adreslerinolursunuz. Örneğin, URI <https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders>, `CustomerID` bir değeri olan müşteriyle ilişkili `Northwind` veri hizmetindeki tüm siparişleri döndürür `ALFKI.`  
  
 Sorgu ifadeleri, filtreleme, sıralama ve sayfalama gibi kaynaklara karşı geleneksel sorgu işlemleri gerçekleştirmenize olanak tanır. Örneğin, URI <https://services.odata.org/Northwind/Northwind.svc/Customers( ' ALFKI ')/Orders? $filter = Nakliye gt 50 >, kaynakları yalnızca $50 'den daha fazla nakliye maliyeti olan siparişleri döndürecek şekilde filtreler. Daha fazla bilgi için bkz. [veri hizmeti kaynaklarına erişme](accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Birlikte çalışabilen veri erişimi  
 OData, veri hizmetlerini .NET Framework kullanmayan uygulamalarla birlikte çalışabilir hale getirmek için standart Internet protokollerinde oluşturulur. Verileri adresleyerek standart URI 'Leri kullanabilmeniz için, uygulamanız temsili durum aktarımı (REST) semantiğini kullanarak verilere erişebilir ve değiştirebilir, özellikle Al, koy, POST ve DELETE için standart HTTP fiilleri. Bu, standart HTTP protokolleri üzerinden aktarılan verileri ayrıştırabilen ve bunlara erişebilen herhangi bir istemciden bu hizmetlere erişmenizi sağlar.  
  
OData, Atom yayımlama Protokolü (AtomPub) için bir uzantılar kümesi tanımlar. Çeşitli istemci uygulamalarına ve platformlarına uyum sağlamak için birden fazla veri biçimindeki HTTP isteklerini ve yanıtlarını destekler. OData akışı, atom, JavaScript Nesne Gösterimi (JSON) ve düz XML olarak verileri temsil edebilir. Atom varsayılan biçim olsa da akışın biçimi HTTP isteğinin üst bilgisinde belirtilir. Daha fazla bilgi için bkz. [OData: Atom biçimi](https://www.odata.org/documentation/odata-version-2-0/atom-format/) ve [OData: JSON biçimi](https://www.odata.org/documentation/odata-version-2-0/json-format/).  
  
 Verileri OData akışı olarak yayımlarken WCF Veri Hizmetleri, önbelleğe alma ve kimlik doğrulama gibi diğer mevcut Internet tesislerini kullanır. Bunu gerçekleştirmek için, ASP.NET, Windows Communication Foundation (WCF) ve Internet Information Services (IIS) gibi mevcut barındırma uygulamaları ve hizmetleriyle tümleştirilir WCF Veri Hizmetleri.  
  
## <a name="storage-independence"></a>Depolama bağımsızlık  
 Kaynaklar bir varlık ilişkisi modeline göre değinse de WCF Veri Hizmetleri, temel alınan veri kaynağından bağımsız olarak OData akışlarını kullanıma sunar. WCF Veri Hizmetleri, URI tarafından tanımlanan bir kaynak için HTTP isteğini kabul ettikten sonra, istek seri durumdan çıkarılmış olur ve bu isteğin temsili bir WCF Veri Hizmetleri sağlayıcısına geçirilir. Bu sağlayıcı, isteği veri kaynağına özgü biçime çevirir ve isteği temel alınan veri kaynağında yürütür. WCF Veri Hizmetleri, OData tarafından önceden belirlenmiş kaynaklara yönelik kavramsal modeli, temel alınan veri kaynağının belirli bir şemasından ayırarak depolama bağımsızlık kaynağına erişir.  
  
 WCF Veri Hizmetleri, ilişkisel verileri kullanıma sunan veri Hizmetleri oluşturmanıza olanak tanımak için ADO.NET Entity Framework ile tümleşir. Varlık olarak adreslenebilir kaynakları içeren bir veri modeli oluşturmak için Varlık Veri Modeli araçlarını kullanabilirsiniz ve aynı zamanda bu model ile temel alınan veritabanındaki tablolar arasındaki eşlemeyi tanımlar. Daha fazla bilgi için bkz. [Entity Framework sağlayıcısı](entity-framework-provider-wcf-data-services.md).  
  
 WCF Veri Hizmetleri ayrıca, <xref:System.Linq.IQueryable%601> arabiriminin bir uygulamasını döndüren veri yapılarını sunan veri Hizmetleri oluşturmanıza olanak sağlar. Bu, .NET Framework türlerindeki verileri kullanıma sunan veri Hizmetleri oluşturmanıza olanak sağlar. Oluşturma, güncelleştirme ve silme işlemleri, <xref:System.Data.Services.IUpdatable> arabirimini de uyguladığınızda desteklenir. Daha fazla bilgi için bkz. [yansıma sağlayıcısı](reflection-provider-wcf-data-services.md).  
  
 WCF Veri Hizmetleri bu veri sağlayıcılarıyla nasıl tümleştirildiğini gösteren bir çizim için, bu konunun ilerleyen kısımlarında bulunan mimari diyagrama bakın.  
  
## <a name="custom-business-logic"></a>Özel Iş mantığı  
 WCF Veri Hizmetleri, hizmet işlemleri ve yakalayıcılar aracılığıyla bir veri hizmetine özel iş mantığı eklemenizi kolaylaştırır. Hizmet işlemleri, veri kaynaklarıyla aynı formda bulunan URI 'Ler tarafından adreslenebilir sunucuda tanımlanmış yöntemlerdir. Hizmet işlemleri bir işlemin döndürdüğü verileri filtrelemek, sıralamak ve sayfa verilerine yönelik sorgu ifadesi söz dizimini da kullanabilir. Örneğin, URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10`, `OrderDate`Londra 'dan müşteriler için siparişleri döndüren Northwind veri hizmeti üzerinde `GetOrdersByCity` adlı bir hizmet işleminin çağrısını temsil eder. Daha fazla bilgi için bkz. [hizmet işlemleri](service-operations-wcf-data-services.md).  
  
 Yakalayıcılar, bir veri hizmeti tarafından istek veya yanıt iletilerinin işlenmesinde tümleştirilecek özel uygulama mantığını etkinleştirir. Belirtilen varlık kümesinde bir sorgu, ekleme, güncelleştirme veya silme eylemi gerçekleştiğinde, bu dinleyici çağrılır. Daha sonra bir dinleyici, verileri değiştirebilir, yetkilendirme ilkesini uygulayabilir veya hatta işlemi sonlandırır. Bir veri hizmeti tarafından kullanıma sunulan belirli bir varlık kümesi için yakalayıcıyı yöntemleri açık olarak kaydedilmelidir. Daha fazla bilgi için bkz. [yakalayıcılar](interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>İstemci Kitaplıkları  
 OData, veri hizmetleriyle etkileşim kurmak için bir Tekdüzen desenleri kümesi tanımlar. Bu, veri hizmetlerini kullanmayı kolaylaştıran istemci tarafı kitaplıkları gibi bu hizmetlere dayalı yeniden kullanılabilir bileşenler oluşturmaya yönelik bir fırsat sağlar.  
  
 WCF Veri Hizmetleri hem .NET Framework tabanlı hem de Silverlight tabanlı istemci uygulamaları için istemci kitaplıkları içerir. Bu istemci kitaplıkları .NET Framework nesneleri kullanarak veri hizmetleriyle etkileşim kurmanızı sağlar. Bunlar ayrıca nesne tabanlı sorguları ve LINQ sorgularını, ilgili nesneleri, değişiklik izlemeyi ve kimlik çözümlemesini destekler. Daha fazla bilgi için [WCF veri Hizmetleri Istemci kitaplığı](wcf-data-services-client-library.md)' na bakın.  
  
 .NET Framework ve Silverlight ile birlikte bulunan OData istemci kitaplıklarına ek olarak, PHP, AJAX ve Java uygulamaları gibi istemci uygulamalarında bir OData akışını kullanmanıza olanak tanıyan başka istemci kitaplıkları da vardır. OData SDK hakkında daha fazla bilgi için bkz. [OData SDK-örnek kodu](https://www.odata.org/ecosystem/#sdk).
  
## <a name="architecture-overview"></a>Mimariye Genel Bakış  
 Aşağıdaki diyagramda OData akışlarını gösterme ve OData özellikli istemci kitaplıklarında bu akışları kullanma WCF Veri Hizmetleri mimarisi gösterilmektedir:  
  
 ![WCF Veri Hizmetleri mimari diyagramını gösteren ekran görüntüsü.](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri 4.5](index.md)
- [Başlarken](getting-started-with-wcf-data-services.md)
- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [Veri hizmeti kaynaklarına erişme (WCF Veri Hizmetleri)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Temsili durum aktarımı (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
