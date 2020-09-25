---
title: Ertelenmiş Içerik yükleniyor (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 32f9b588-c832-44c4-a7e0-fcce635df59a
ms.openlocfilehash: 6eff454bf4f79f7fe215828956ffe79d0c1f6757
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194329"
---
# <a name="loading-deferred-content-wcf-data-services"></a>Ertelenmiş Içerik yükleniyor (WCF Veri Hizmetleri)

Varsayılan olarak, WCF Veri Hizmetleri bir sorgunun döndürdüğü veri miktarını sınırlandırır. Ancak, gerekli olduğunda veri hizmetinden ilgili varlıklar, sayfalama yanıtı verileri ve ikili veri akışları dahil ek verileri açıkça yükleyebilirsiniz. Bu konu, bu tür ertelenmiş içeriğin uygulamanıza nasıl yükleneceğini açıklar.  
  
## <a name="related-entities"></a>İlgili varlıklar  

 Bir sorgu yürüttüğünüzde, yalnızca belirtilen varlık kümesindeki varlıklar döndürülür. Örneğin, Northwind Data Service 'e yönelik bir sorgu `Customers` varlıkları döndürdüğünde, `Orders` ve arasında bir ilişki olsa da, ilgili varlıklar varsayılan olarak döndürülmez `Customers` `Orders` . Ayrıca, veri hizmetinde sayfalama etkin olduğunda, sonraki veri sayfalarını hizmetten açıkça yüklemeniz gerekir. İlgili varlıkları yüklemek için iki yol vardır:  
  
- **Ekip yükleme**: sorgu, sorgunun `$expand` istediği varlık kümesine yönelik bir ilişki ile ilişkili varlıkları döndürmesini istemek için sorgu seçeneğini kullanabilirsiniz. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> <xref:System.Data.Services.Client.DataServiceQuery%601> `$expand` Veri hizmetine gönderilen sorguya seçeneği eklemek için üzerinde yöntemini kullanın. Aşağıdaki örnekte olduğu gibi, bunları virgülle ayırarak birden çok ilgili varlık kümesi isteyebilirsiniz. Sorgu tarafından istenen tüm varlıklar tek bir yanıtta döndürülür. Aşağıdaki örnek, `Order_Details` `Customers` varlık kümesiyle birlikte ve birlikte döndürür `Orders` :  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetailsspecific)]  
  
     Sorgu seçeneği kullanılarak tek bir sorguya dahil edilebilir olan varlık kümesi sayısını 12 ' ye WCF Veri Hizmetleri kısıtlar `$expand` .  
  
- **Açık yükleme**: <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> <xref:System.Data.Services.Client.DataServiceContext> ilgili varlıkları açıkça yüklemek için örneğinde yöntemi çağırabilirsiniz. Yöntemine yapılan her çağrı <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> , veri hizmetine ayrı bir istek oluşturur. Aşağıdaki örnek `Order_Details` bir varlık için açıkça yüklenir `Orders` :  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Hangi seçeneği kullanacağınızı göz önünde bulundurmanız durumunda, veri hizmetine yapılan istek sayısı ve tek bir yanıtta döndürülen veri miktarı arasında bir zorunluluğunu getirir olduğunu unutmayın. Uygulamanız ilişkili nesneler gerektirdiğinde ve ek isteklerin açıkça alınması için ek gecikme süresinin oluşmasını önlemek istediğinizde, Eager yükleme kullanın. Ancak, uygulamanın yalnızca belirli varlık örnekleri için verileri ihtiyacı olduğunda, yöntemi çağırarak bu varlıkları açıkça yüklemeyi göz önünde bulundurmanız gerekir <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> . Daha fazla bilgi için bkz. [nasıl yapılır: Ilgili varlıkları yükleme](how-to-load-related-entities-wcf-data-services.md).  
  
## <a name="paged-content"></a>Disk belleğine alınmış Içerik  

 Veri hizmetinde sayfalama etkin olduğunda, veri hizmetinin döndürdüğü akıştaki giriş sayısı veri hizmetinin yapılandırmasıyla sınırlıdır. Sayfa sınırları her bir varlık kümesi için ayrı ayrı ayarlanabilir. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md). Sayfalama etkinleştirildiğinde akıştaki son giriş, bir sonraki veri sayfasına bir bağlantı içerir. Bu bağlantı bir nesne içinde yer alır <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> . Bir sonraki veri sayfasına URI 'yi <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> , yürütüldüğünde döndürülen üzerinde yöntemini çağırarak elde edersiniz <xref:System.Data.Services.Client.QueryOperationResponse%601> <xref:System.Data.Services.Client.DataServiceQuery%601> . Döndürülen <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> nesne daha sonra sonuçların sonraki sayfasını yüklemek için kullanılır. Yöntemi çağırmadan önce sorgu sonucunu numaralandırabilirsiniz gerekir <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> . `do…while`İlk olarak sorgu sonucunu numaralandırmak ve sonra bir sonraki bağlantı değerini denetlemek için bir döngü kullanmayı düşünün `non-null` . <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A>Yöntem döndüğünde `null` ( `Nothing` Visual Basic), özgün sorgu için ek sonuç sayfası yoktur. Aşağıdaki örnekte, `do…while` Northwind örnek veri hizmetinden disk belleğine alınmış müşteri verileri yükleyen bir döngü gösterilmektedir.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextlink)]  
  
 Bir sorgu, ilgili varlıkların istenen varlık kümesiyle birlikte tek bir yanıtta döndürüldüğü zaman, sayfalama sınırları, yanıtla birlikte satır içi olan iç içe akışları etkileyebilir. Örneğin, varlık kümesi için Northwind örnek veri hizmetinde bir sayfalama sınırı ayarlandığında `Customers` , `Orders` Northwind örnek veri hizmetini tanımlayan Northwind.svc.cs dosyasından aşağıdaki örnekte olduğu gibi ilgili varlık kümesi için de bağımsız bir sayfalama sınırı ayarlanabilir.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 Bu durumda, hem üst düzey `Customers` hem de iç içe varlık akışları için sayfalama uygulamanız gerekir `Orders` . Aşağıdaki örnek, `while` `Orders` Seçilen bir varlıkla ilgili varlıkların sayfalarını yüklemek için kullanılan döngüyü gösterir `Customers` .  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextorderslink)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: Sayfalanmış sonuçları yükleme](how-to-load-paged-results-wcf-data-services.md).  
  
## <a name="binary-data-streams"></a>İkili veri akışları  

 WCF Veri Hizmetleri, ikili büyük nesne (BLOB) verilerine veri akışı olarak erişmenizi sağlar. Akış, gerekli olana kadar ikili verilerin yüklenmesini erteler ve istemci bu verileri daha verimli bir şekilde işleyebilir. Bu işlevden yararlanmak için, veri hizmetinin sağlayıcıyı uygulaması gerekir <xref:System.Data.Services.Providers.IDataServiceStreamProvider> . Daha fazla bilgi için bkz. [Akış sağlayıcısı](streaming-provider-wcf-data-services.md). Akış etkinleştirildiğinde, varlık türleri ilgili ikili veriler olmadan döndürülür. Bu durumda, <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> <xref:System.Data.Services.Client.DataServiceContext> hizmetten gelen ikili veriler için veri akışına erişmek üzere sınıfının yöntemini kullanmanız gerekir. Benzer şekilde, <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> bir varlık için ikili verileri bir akış olarak eklemek veya değiştirmek için yöntemini kullanın. Daha fazla bilgi için bkz. [Ikili verilerle çalışma](working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
