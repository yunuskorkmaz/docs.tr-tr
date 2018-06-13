---
title: İçerik (WCF Veri Hizmetleri) yükleme ertelenmiş
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 32f9b588-c832-44c4-a7e0-fcce635df59a
ms.openlocfilehash: 8ab4dea9e4f687f9548bb2b46a8f6baf428e29af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365208"
---
# <a name="loading-deferred-content-wcf-data-services"></a>İçerik (WCF Veri Hizmetleri) yükleme ertelenmiş
Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir sorgunun döndürdüğü veri miktarını sınırlar. Ancak, ilişkili varlıklar, disk belleğine alınan yanıt verilerini ve gerektiğinde veri hizmetinden ikili veri akışlarını gibi ek veriler açıkça yükleyebilirsiniz. Bu konu, uygulamanıza ertelenmiş tür içeriği yüklemek açıklar.  
  
## <a name="related-entities"></a>İlgili varlıklar  
 Bir sorgu yürütülürken yalnızca adresli varlık kümesindeki varlıklar döndürülür. Örneğin, Northwind veri hizmeti bir sorgu döndüğünde `Customers` varlıklar, varsayılan olarak ilgili `Orders` varlıklar alınmadı, arasında bir ilişki olsa bile `Customers` ve `Orders`. Ayrıca, disk belleği veri hizmeti etkinleştirildiğinde, hizmetten sonraki veri sayfaları açıkça yüklemelisiniz. İlgili varlıklar yüklemek için iki yol vardır:  
  
-   **İstekli yükleme**: kullanabileceğiniz `$expand` sorgu varlık için bir ilişki ile ilişkilendirilen varlıkları döndürme istek için sorgu seçeneği ayarlayın, istenen sorgu. Kullanım <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yöntemi <xref:System.Data.Services.Client.DataServiceQuery%601> eklemek için `$expand` veri hizmetine gönderilen sorgu seçeneği. Aşağıdaki örnekte olduğu gibi bir virgül ile ayırarak birden fazla ilgili varlık ayarlar isteyebilir. Sorgu tarafından istenen tüm varlıkları tek bir yanıt olarak döndürülür. Aşağıdaki örnek verir `Order_Details` ve `Customers` ile birlikte `Orders` varlık kümesi:  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#expandorderdetailsspecific)]  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 12 için tek bir sorgu kullanarak eklenebilir varlık kümeleri sayısını sınırlar `$expand` sorgu seçeneği.  
  
-   **Açık yükleme**: çağırabilirsiniz <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext> açıkça ilgili varlıklar yüklemek için örnek. Her çağrı <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> yöntemi, veri hizmeti için ayrı bir istek oluşturur. Aşağıdaki örnek açıkça yükler `Order_Details` için bir `Orders` varlık:  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Hangi seçeneğin kullanılacağını düşünürken, veri hizmeti için istek sayısı ve tek bir yanıtta döndürülen veri miktarını arasında kolaylığını olduğunu unutmayın. İlişkili nesneleri uygulamanızın gerektirdiği ve açıkça bunları almak için ek istekler eklenen gecikmesi engellemek istediğinizde istekli yüklenirken kullanın. Uygulama için belirli ilgili varlık örnek verileri yalnızca gerektiğinde durumlarda varsa ancak, açıkça çağırarak bu varlıkların yüklenirken düşünmelisiniz <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> yöntemi. Daha fazla bilgi için bkz: [nasıl yapılır: yük ilgili varlıklar](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md).  
  
## <a name="paged-content"></a>Disk belleğine alınan içerik  
 Disk belleği veri hizmeti etkinleştirildiğinde, veri hizmeti yapılandırma tarafından veri döndürür hizmeti akıştaki girdi sayısı sınırlıdır. Sayfa sınırlarını ayrı ayrı her varlık kümesi için ayarlayabilirsiniz. Daha fazla bilgi için bkz: [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Sayfalama etkin olduğunda, son girişi akıştaki verilerin bir sonraki sayfaya bir bağlantı içerir. Bu bağlantıyı içeren bir <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> nesnesi. Öğesini çağırarak verilerin bir sonraki sayfaya URI elde <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> yöntemi <xref:System.Data.Services.Client.QueryOperationResponse%601> olduğunda döndürülen <xref:System.Data.Services.Client.DataServiceQuery%601> yürütülür. Döndürülen <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> nesnesi sonraki sonuç sayfasını yüklemek için daha sonra kullanılır. Çağırmadan önce sorgu sonucu listeleme <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> yöntemi. Kullanmayı bir `do…while` ilk sorgu sonucu numaralandırmak ve ardından denetlemek için döngü bir `non-null` değeri'sonraki bağlantı. Zaman <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> yöntemi döndürür `null` (`Nothing` Visual Basic'te), özgün sorgu için ek sonuç sayfa yok. Aşağıdaki örnekte gösterildiği bir `do…while` yükler döngü, Northwind örnek veri hizmetinden müşteri verileri disk belleğine alınan.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadnextlink)]  
  
 İstenen varlık kümesi ile birlikte tek bir yanıt varlıkları ile ilgili bir sorgu isteği döndürüldüğünde, disk belleği sınırları dahil satır içi yanıt iç içe geçmiş akışları etkileyebilir. Örneğin, bir disk belleği sınırı ayarlandığında Northwind örnek veri hizmetinde `Customers` varlık kümesi, bağımsız bir disk belleği sınırını da ayarlayabilirsiniz ilgili için `Orders` varlık kümesi, Northwind.svc.cs aşağıdaki örnekte olduğu gibi dosya Northwind örnek veri hizmeti tanımlar.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 Bu durumda, her iki üst düzey için disk belleği uygulamalıdır `Customers` ve iç içe `Orders` varlık akışları. Aşağıdaki örnekte gösterildiği `while` sayfaları yüklemek için kullanılan döngü `Orders` varlıkları ile ilgili bir seçili `Customers` varlık.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadnextorderslink)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: yük disk belleğine alınan sonuçları](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md).  
  
## <a name="binary-data-streams"></a>İkili veri akışları  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir veri akışı olarak ikili büyük nesne (BLOB) veri erişim sağlar. Akış ikili veri yüklenmesi gerekli değildir ve istemci bu verileri daha verimli bir şekilde işleyebilir kadar erteler. Bu işlevsellikten yararlanmak için veri hizmeti uygulanması gereken <xref:System.Data.Services.Providers.IDataServiceStreamProvider> sağlayıcısı. Daha fazla bilgi için bkz: [Akış sağlayıcısı](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md). Akış etkinleştirildiğinde, varlık türleri ilgili ikili veriler döndürülür. Bu durumda, kullanmalısınız <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext> ikili veriler için veri akışı hizmetinden erişmek için sınıf. Benzer şekilde, kullanın <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> ekleyin veya ikili veri akışı olarak bir varlık için değiştirmek için bir yöntem. Daha fazla bilgi için bkz: [ikili verileri ile çalışma](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
