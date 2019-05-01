---
title: Ertelenmiş içerik (WCF Veri Hizmetleri) yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 32f9b588-c832-44c4-a7e0-fcce635df59a
ms.openlocfilehash: ee7b0b40d74d908dc4f25372273f852662370df0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037139"
---
# <a name="loading-deferred-content-wcf-data-services"></a>Ertelenmiş içerik (WCF Veri Hizmetleri) yükleme
Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir sorgunun döndürdüğü veri miktarını sınırlar. Ancak, ilgili varlıkları, disk belleğine alınan yanıt verileri ve gerektiğinde veri hizmetinden ikili veri akışları gibi ek veriler açıkça yükleyebilirsiniz. Bu konu, uygulamanıza böyle ertelenmiş içerik yükleme açıklar.  
  
## <a name="related-entities"></a>İlgili varlıklar  
 Bir sorgu çalıştırdığınızda, yalnızca belirtilen varlık kümesindeki varlıklar döndürülür. Örneğin, Northwind verileri hizmeti yönelik bir sorgu döndürdüğünde `Customers` varsayılan olarak ilgili varlıkları `Orders` varlıkları alınmadı, arasında bir ilişki olsa bile `Customers` ve `Orders`. Ayrıca, disk belleği veri hizmeti etkinleştirildiğinde, hizmetten sonraki veri sayfaları açıkça yüklemelisiniz. İlgili varlıkları yükleme için iki yol vardır:  
  
- **İstekli yükleme**: Kullanabileceğiniz `$expand` sorgu ilişkilendirme varlığı için ilişkili olan varlıkları iade isteği için sorgu seçeneği, istenen sorgu ayarlayın. Kullanım <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metodunda <xref:System.Data.Services.Client.DataServiceQuery%601> eklemek için `$expand` veri hizmetine gönderilen sorgu seçeneği. Aşağıdaki örnekte olduğu gibi virgülle ayrılarak birden çok ilgili varlık kümeleri isteyebilir. Sorgu tarafından istenen tüm varlıkları tek bir yanıtta döndürülür. Aşağıdaki örnek döndürür `Order_Details` ve `Customers` ile birlikte `Orders` varlık kümesi:  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetailsspecific)]  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 12 kullanarak tek bir sorguda eklenebilir varlık kümeleri sayısını sınırlayan `$expand` sorgu seçeneği.  
  
- **Açık yükleme**: Çağırabilirsiniz <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metodunda <xref:System.Data.Services.Client.DataServiceContext> açıkça ilgili varlıkları yükleme örneği. Her çağrı <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> yöntemi, veri hizmeti için ayrı bir istek oluşturur. Aşağıdaki örnek açıkça yükler `Order_Details` için bir `Orders` varlık:  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Hangi seçeneğin kullanılacağını düşünürken, veri hizmetine istek sayısı ve tek bir yanıtta döndürülen veri miktarını arasında bir denge olduğunu unutmayın. İstekli yükleme ilişkili nesneleri uygulamanızın gerektirdiği ve açıkça bunları almak için ek istekler eklenen gecikme süresini önlemek istediğinizde kullanın. Uygulamasının belirli ilgili varlık örnekleri için verileri yalnızca gerektiğinde çalışmaları varsa ancak açıkça çağrılarak bu varlıklar yükleniyor dikkate almanız gereken <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> yöntemi. Daha fazla bilgi için [nasıl yapılır: İlgili varlıkları yükleme](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md).  
  
## <a name="paged-content"></a>Disk belleğine alınan içeriği  
 Veri hizmetinde sayfalama etkin olduğunda, veri hizmeti yapılandırması tarafından veri döndürür hizmet akışta girdi sayısı sınırlıdır. Sayfa sınırlarını ayrı olarak her varlık kümesi için ayarlanabilir. Daha fazla bilgi için [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Sayfalama etkin olduğunda, son girişi akıştaki verilerin bir sonraki sayfaya bir bağlantı içerir. Bu bağlantıyı yer alan bir <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> nesne. Sonraki sayfaya veri URI'si çağırarak elde <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metodunda <xref:System.Data.Services.Client.QueryOperationResponse%601> olduğunda döndürülen <xref:System.Data.Services.Client.DataServiceQuery%601> yürütülür. Döndürülen <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> nesne ardından sonraki sonuç sayfasını yüklemek için kullanılır. Çağırmadan önce sorgu sonucu listeleme <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> yöntemi. Kullanmayı bir `do…while` döngü ilk sorgu sonucu sıralaması ve ardından denetlemek için bir `non-null` değeri'sonraki bağlantı. Zaman <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> yöntemi döndürür `null` (`Nothing` Visual Basic'te), özgün sorgu için ek sonuç sayfa yok. Aşağıdaki örnekte gösterildiği bir `do…while` yükler döngü, Northwind örnek veri hizmetinden müşteri verileri disk belleğine alınan.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextlink)]  
  
 İlgili varlıklar bir sorgu isteği istenen varlık kümesi ile birlikte tek bir yanıt döndürüldüğünde, disk belleği sınırı ile yanıtı satır içi olan iç içe geçmiş akışları etkileyebilir. Örneğin, disk belleği sınırı ayarlandığında Northwind örnek veri hizmetinde `Customers` varlık kümesi, bağımsız bir disk belleği sınırını da ayarlayabilirsiniz için ilgili `Orders` varlık kümesi, Northwind.svc.cs aşağıdaki örnekte olduğu gibi dosya Northwind örnek veri hizmeti tanımlar.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 Bu durumda, her iki üst düzey için disk belleği uygulamalıdır `Customers` ve iç içe `Orders` varlık akışları. Aşağıdaki örnekte gösterildiği `while` sayfaları yüklemek için kullanılan döngü `Orders` varlıklar için Seçili ilgili `Customers` varlık.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextorderslink)]  
  
 Daha fazla bilgi için [nasıl yapılır: Sayfalanmış sonuçları yükleme](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md).  
  
## <a name="binary-data-streams"></a>İkili veri akışları  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir veri akışı olarak ikili büyük nesne (BLOB) veri erişim sağlar. Akış ikili verileri yüklenmesi gereken ve istemci bu verileri daha verimli bir şekilde işleyebilir kadar erteler. Bu işlevsellikten yararlanmak için veri hizmeti uygulanması gereken <xref:System.Data.Services.Providers.IDataServiceStreamProvider> sağlayıcısı. Daha fazla bilgi için [Akış sağlayıcısı](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md). Akış etkinleştirildiğinde, varlık türleri ilgili ikili verileri döndürülür. Bu durumda, kullanmalısınız <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext> ikili veriler için veri akışı erişmenize izin sınıfı. Benzer şekilde, kullanmak <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> eklemek veya ikili veri akışı olarak bir varlığın değiştirmek için yöntemi. Daha fazla bilgi için [ikili verilerle çalışma](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
