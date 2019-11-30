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
ms.openlocfilehash: 811118755c4688bd0ea8cb9ba37b2101ab6c52cf
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568950"
---
# <a name="loading-deferred-content-wcf-data-services"></a>Ertelenmiş Içerik yükleniyor (WCF Veri Hizmetleri)
Varsayılan olarak, WCF Veri Hizmetleri bir sorgunun döndürdüğü veri miktarını sınırlandırır. Ancak, gerekli olduğunda veri hizmetinden ilgili varlıklar, sayfalama yanıtı verileri ve ikili veri akışları dahil ek verileri açıkça yükleyebilirsiniz. Bu konu, bu tür ertelenmiş içeriğin uygulamanıza nasıl yükleneceğini açıklar.  
  
## <a name="related-entities"></a>İlgili varlıklar  
 Bir sorgu yürüttüğünüzde, yalnızca belirtilen varlık kümesindeki varlıklar döndürülür. Örneğin, Northwind Data Service 'e yönelik bir sorgu `Customers` varlıkları döndürdüğünde, `Customers` ve `Orders`arasında bir ilişki olsa da, ilgili `Orders` varlıkları varsayılan olarak döndürülmez. Ayrıca, veri hizmetinde sayfalama etkin olduğunda, sonraki veri sayfalarını hizmetten açıkça yüklemeniz gerekir. İlgili varlıkları yüklemek için iki yol vardır:  
  
- **Ekip yükleme**: sorgunun istediği varlık kümesine yönelik bir ilişki ile ilişkili varlıkları döndürmesini istemek için `$expand` sorgu seçeneğini kullanabilirsiniz. Veri hizmetine gönderilen sorguya `$expand` seçeneğini eklemek için <xref:System.Data.Services.Client.DataServiceQuery%601> <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yöntemi kullanın. Aşağıdaki örnekte olduğu gibi, bunları virgülle ayırarak birden çok ilgili varlık kümesi isteyebilirsiniz. Sorgu tarafından istenen tüm varlıklar tek bir yanıtta döndürülür. Aşağıdaki örnek, `Orders` varlık kümesiyle birlikte `Order_Details` ve `Customers` döndürür:  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetailsspecific)]  
  
     WCF Veri Hizmetleri, `$expand` sorgu seçeneği kullanılarak tek bir sorguya dahil edilebilir olan varlık kümesi sayısını 12 ile sınırlar.  
  
- **Açık yükleme**: ilgili varlıkları açıkça yüklemek için <xref:System.Data.Services.Client.DataServiceContext> örneğinde <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> yöntemini çağırabilirsiniz. <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> yöntemine yapılan her bir çağrı, veri hizmetine ayrı bir istek oluşturur. Aşağıdaki örnek, `Orders` bir varlık için `Order_Details` açık olarak yükler:  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Hangi seçeneği kullanacağınızı göz önünde bulundurmanız durumunda, veri hizmetine yapılan istek sayısı ve tek bir yanıtta döndürülen veri miktarı arasında bir zorunluluğunu getirir olduğunu unutmayın. Uygulamanız ilişkili nesneler gerektirdiğinde ve ek isteklerin açıkça alınması için ek gecikme süresinin oluşmasını önlemek istediğinizde, Eager yükleme kullanın. Ancak, uygulamanın yalnızca belirli varlık örnekleri için verileri ihtiyacı olan durumlar varsa, <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> yöntemini çağırarak bu varlıkları açıkça yüklemeyi göz önünde bulundurmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: Ilgili varlıkları yükleme](how-to-load-related-entities-wcf-data-services.md).  
  
## <a name="paged-content"></a>Disk belleğine alınmış Içerik  
 Veri hizmetinde sayfalama etkin olduğunda, veri hizmetinin döndürdüğü akıştaki giriş sayısı veri hizmetinin yapılandırmasıyla sınırlıdır. Sayfa sınırları her bir varlık kümesi için ayrı ayrı ayarlanabilir. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md). Sayfalama etkinleştirildiğinde akıştaki son giriş, bir sonraki veri sayfasına bir bağlantı içerir. Bu bağlantı <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> nesnesinde yer alır. <xref:System.Data.Services.Client.DataServiceQuery%601> yürütüldüğünde döndürülen <xref:System.Data.Services.Client.QueryOperationResponse%601> <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> yöntemini çağırarak URI 'yi bir sonraki veri sayfasına elde edersiniz. Döndürülen <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> nesnesi daha sonra sonuçların sonraki sayfasını yüklemek için kullanılır. <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> yöntemini çağırmadan önce sorgu sonucunu numaralandırabilirsiniz gerekir. İlk olarak sorgu sonucunu numaralandırmak için bir `do…while` döngüsü kullanmayı düşünün ve sonra bir sonraki `non-null` bağlantı değerini kontrol edin. <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> yöntemi `null` (`Nothing` Visual Basic) döndürürse, özgün sorgu için ek sonuç sayfası yoktur. Aşağıdaki örnek, Northwind örnek veri hizmetinden disk belleğine alınmış müşteri verileri yükleyen bir `do…while` döngüsünü gösterir.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextlink)]  
  
 Bir sorgu, ilgili varlıkların istenen varlık kümesiyle birlikte tek bir yanıtta döndürüldüğü zaman, sayfalama sınırları, yanıtla birlikte satır içi olan iç içe akışları etkileyebilir. Örneğin, `Customers` varlık kümesi için Northwind örnek veri hizmetinde bir sayfalama sınırı ayarlandığında, Northwind örnek veri hizmetini tanımlayan Northwind.svc.cs dosyasından aşağıdaki örnekte olduğu gibi, ilgili `Orders` varlık kümesi için de bağımsız bir sayfalama sınırı ayarlanabilir.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 Bu durumda, hem üst düzey `Customers` hem de iç içe `Orders` varlık akışları için sayfalama uygulamanız gerekir. Aşağıdaki örnek, seçilen bir `Customers` varlığıyla ilgili `Orders` varlıklarının sayfalarını yüklemek için kullanılan `while` döngüsünü gösterir.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextorderslink)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: Sayfalanmış sonuçları yükleme](how-to-load-paged-results-wcf-data-services.md).  
  
## <a name="binary-data-streams"></a>İkili veri akışları  
 WCF Veri Hizmetleri, ikili büyük nesne (BLOB) verilerine veri akışı olarak erişmenizi sağlar. Akış, gerekli olana kadar ikili verilerin yüklenmesini erteler ve istemci bu verileri daha verimli bir şekilde işleyebilir. Bu işlevden faydalanmak için, veri hizmetinin <xref:System.Data.Services.Providers.IDataServiceStreamProvider> sağlayıcıyı uygulaması gerekir. Daha fazla bilgi için bkz. [Akış sağlayıcısı](streaming-provider-wcf-data-services.md). Akış etkinleştirildiğinde, varlık türleri ilgili ikili veriler olmadan döndürülür. Bu durumda, hizmetten gelen ikili verilerin veri akışına erişmek için <xref:System.Data.Services.Client.DataServiceContext> sınıfının <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> yöntemini kullanmanız gerekir. Benzer şekilde, bir varlık için ikili verileri bir akış olarak eklemek veya değiştirmek için <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> yöntemini kullanın. Daha fazla bilgi için bkz. [Ikili verilerle çalışma](working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
