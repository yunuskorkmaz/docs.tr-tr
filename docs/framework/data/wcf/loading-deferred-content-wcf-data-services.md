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
ms.openlocfilehash: 7c53ad18e029dbe1f882035c1bffc8f4bfbaa2f9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790417"
---
# <a name="loading-deferred-content-wcf-data-services"></a>Ertelenmiş Içerik yükleniyor (WCF Veri Hizmetleri)
Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir sorgunun döndürdüğü veri miktarını sınırlandırır. Ancak, gerekli olduğunda veri hizmetinden ilgili varlıklar, sayfalama yanıtı verileri ve ikili veri akışları dahil ek verileri açıkça yükleyebilirsiniz. Bu konu, bu tür ertelenmiş içeriğin uygulamanıza nasıl yükleneceğini açıklar.  
  
## <a name="related-entities"></a>İlgili varlıklar  
 Bir sorgu yürüttüğünüzde, yalnızca belirtilen varlık kümesindeki varlıklar döndürülür. Örneğin, Northwind Data Service 'e yönelik bir sorgu `Customers` varlıkları döndürdüğünde, ve `Orders`arasında `Customers` bir ilişki olsa da `Orders` , ilgili varlıklar varsayılan olarak döndürülmez. Ayrıca, veri hizmetinde sayfalama etkin olduğunda, sonraki veri sayfalarını hizmetten açıkça yüklemeniz gerekir. İlgili varlıkları yüklemek için iki yol vardır:  
  
- **Ekip yükleme**: Sorgunun istediği varlık kümesine `$expand` yönelik bir ilişki ile ilişkili varlıkları döndürmesini istemek için sorgu seçeneğini kullanabilirsiniz. Veri hizmetine gönderilen sorguya `$expand` seçeneği <xref:System.Data.Services.Client.DataServiceQuery%601> eklemek için üzerinde yönteminikullanın.<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Aşağıdaki örnekte olduğu gibi, bunları virgülle ayırarak birden çok ilgili varlık kümesi isteyebilirsiniz. Sorgu tarafından istenen tüm varlıklar tek bir yanıtta döndürülür. Aşağıdaki örnek, `Order_Details` `Orders` varlık kümesiyle `Customers` birlikte ve birlikte döndürür:  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetailsspecific)]  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]`$expand` sorgu seçeneği kullanılarak tek bir sorguya dahil edilebilir varlık kümesi sayısını 12 ile sınırlandırır.  
  
- **Açık yükleme**: İlgili varlıkları açıkça yüklemek <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> için <xref:System.Data.Services.Client.DataServiceContext> örneğinde yöntemi çağırabilirsiniz. <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> Yöntemine yapılan her çağrı, veri hizmetine ayrı bir istek oluşturur. Aşağıdaki örnek bir `Orders` varlık için `Order_Details` açıkça yüklenir:  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Hangi seçeneği kullanacağınızı göz önünde bulundurmanız durumunda, veri hizmetine yapılan istek sayısı ve tek bir yanıtta döndürülen veri miktarı arasında bir zorunluluğunu getirir olduğunu unutmayın. Uygulamanız ilişkili nesneler gerektirdiğinde ve ek isteklerin açıkça alınması için ek gecikme süresinin oluşmasını önlemek istediğinizde, Eager yükleme kullanın. Ancak, uygulamanın yalnızca belirli varlık örnekleri için verileri ihtiyacı olduğunda, <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> yöntemi çağırarak bu varlıkları açıkça yüklemeyi göz önünde bulundurmanız gerekir. Daha fazla bilgi için [nasıl yapılır: Ilgili varlıkları](how-to-load-related-entities-wcf-data-services.md)yükleyin.  
  
## <a name="paged-content"></a>Disk belleğine alınmış Içerik  
 Veri hizmetinde sayfalama etkin olduğunda, veri hizmetinin döndürdüğü akıştaki giriş sayısı veri hizmetinin yapılandırmasıyla sınırlıdır. Sayfa sınırları her bir varlık kümesi için ayrı ayrı ayarlanabilir. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md). Sayfalama etkinleştirildiğinde akıştaki son giriş, bir sonraki veri sayfasına bir bağlantı içerir. Bu bağlantı bir <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> nesne içinde yer alır. Bir sonraki veri sayfasına URI 'yi, <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> <xref:System.Data.Services.Client.DataServiceQuery%601> yürütüldüğünde <xref:System.Data.Services.Client.QueryOperationResponse%601> döndürülen üzerinde yöntemini çağırarak elde edersiniz. Döndürülen <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> nesne daha sonra sonuçların sonraki sayfasını yüklemek için kullanılır. <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> Yöntemi çağırmadan önce sorgu sonucunu numaralandırabilirsiniz gerekir. İlk olarak sorgu `do…while` sonucunu numaralandırmak ve sonra bir `non-null` sonraki bağlantı değerini denetlemek için bir döngü kullanmayı düşünün. Yöntem döndüğünde `null` (`Nothing` Visual Basic), özgün sorgu için ek sonuç sayfası yoktur. <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> Aşağıdaki örnekte, Northwind örnek `do…while` veri hizmetinden disk belleğine alınmış müşteri verileri yükleyen bir döngü gösterilmektedir.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextlink)]  
  
 Bir sorgu, ilgili varlıkların istenen varlık kümesiyle birlikte tek bir yanıtta döndürüldüğü zaman, sayfalama sınırları, yanıtla birlikte satır içi olan iç içe akışları etkileyebilir. Örneğin, `Customers` varlık kümesi için Northwind örnek veri hizmetinde bir sayfalama sınırı ayarlandığında, ilgili `Orders` varlık kümesi için de bağımsız bir disk belleği sınırı ayarlanabilir, bu Northwind.svc.cs dosyasından aşağıdaki örnekte olduğu gibi Northwind örnek veri hizmetini tanımlar.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 Bu durumda, hem üst düzey `Customers` hem de iç içe `Orders` varlık akışları için sayfalama uygulamanız gerekir. Aşağıdaki örnek, seçilen `while` `Customers` bir varlıkla ilgili `Orders` varlıkların sayfalarını yüklemek için kullanılan döngüyü gösterir.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextorderslink)]  
  
 Daha fazla bilgi için [nasıl yapılır: Disk belleğine alınmış](how-to-load-paged-results-wcf-data-services.md)sonuçları yükle.  
  
## <a name="binary-data-streams"></a>İkili veri akışları  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]ikili büyük nesne (BLOB) verilerine veri akışı olarak erişmenizi sağlar. Akış, gerekli olana kadar ikili verilerin yüklenmesini erteler ve istemci bu verileri daha verimli bir şekilde işleyebilir. Bu işlevden yararlanmak için, veri hizmetinin <xref:System.Data.Services.Providers.IDataServiceStreamProvider> sağlayıcıyı uygulaması gerekir. Daha fazla bilgi için bkz. [Akış sağlayıcısı](streaming-provider-wcf-data-services.md). Akış etkinleştirildiğinde, varlık türleri ilgili ikili veriler olmadan döndürülür. Bu durumda, hizmetten gelen ikili veriler için <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> veri akışına erişmek <xref:System.Data.Services.Client.DataServiceContext> üzere sınıfının yöntemini kullanmanız gerekir. Benzer şekilde, bir <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> varlık için ikili verileri bir akış olarak eklemek veya değiştirmek için yöntemini kullanın. Daha fazla bilgi için bkz. [Ikili verilerle çalışma](working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
