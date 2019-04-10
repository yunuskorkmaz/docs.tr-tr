---
title: Veri hizmetini (WCF Veri Hizmetleri) güncelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
- WCF Data Services, client library
ms.assetid: 00d993be-ffed-4dea-baf7-6eea982cdb54
ms.openlocfilehash: 5b8fa13bf5db7f3c3df97febe4bb6f9ee4c184a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231298"
---
# <a name="updating-the-data-service-wcf-data-services"></a>Veri hizmetini (WCF Veri Hizmetleri) güncelleştirme
Kullanırken [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kullanmak için istemci kitaplığı bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akışı, kitaplık istemci veri hizmeti sınıfların örneklerini akış girişleri çevirir. Bu veri hizmeti sınıfları kullanılarak izlenen <xref:System.Data.Services.Client.DataServiceContext> hangi <xref:System.Data.Services.Client.DataServiceQuery%601> ait. İstemcinin, üzerinde yöntemleri kullanarak rapor varlıkları yapılan değişiklikleri izler. <xref:System.Data.Services.Client.DataServiceContext>. Bu yöntemler, eklenen ve Silinen varlıkları ve ayrıca özellik değerlerini veya varlık örnekleri arasında ilişkiler için yaptığınız değişiklikleri izlemek istemci etkinleştirin. Çağırdığınızda bu izlenen değişiklikleri REST tabanlı işlemler veri hizmetine gönderilen <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi.  
  
> [!NOTE]
>  Bir örneğini kullandığınızda, <xref:System.Data.Services.Client.DataServiceCollection%601> verileri denetimlere bağlamak için ilişkili denetim verilerde yapılan değişiklikleri otomatik olarak bildirildiğini <xref:System.Data.Services.Client.DataServiceContext>. Daha fazla bilgi için [denetimlere veri bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
## <a name="adding-modifying-and-changing-entities"></a>Ekleme, değiştirme ve varlıkları değiştirme  
 Kullanırken **hizmet Başvurusu Ekle** iletişim için bir başvuru eklemek için Visual Studio'da bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışı, sonuçta elde edilen istemci veri hizmeti sınıfları her bir statik sahip *Oluştur* alır yöntemi Her değer atanamayan varlık özelliği için parametre. Varlık örneklerini aşağıdaki örnekteki gibi türü sınıfları oluşturmak için bu yöntemi kullanabilirsiniz:  
  
 [!code-csharp[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#createnewproduct)]
 [!code-vb[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#createnewproduct)]  
  
 Bir varlık örneğini eklemek için uygun çağrı *AddTo* metodunda <xref:System.Data.Services.Client.DataServiceContext> sınıfı tarafından oluşturulan **hizmet Başvurusu Ekle** iletişim kutusunda, aşağıdaki örnekte olduğu gibi:  
  
 [!code-csharp[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproductspecific)]
 [!code-vb[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproductspecific)]  
  
 Bu nesne bağlamı ve doğru varlık kümesine ekler. Ayrıca, çağırabilirsiniz <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>, ancak bunun yerine, varlık kümesinin adı sağlamanız gerekir. Eklenen varlığın diğer varlıklarla ilişkiler bir veya daha fazla varsa, kullanabilir <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> yöntemi önceki yöntemlerden birini kullanın veya bu bağlantıları da açıkça tanımlayın. Bu işlemler, bu konunun ilerleyen bölümlerinde ele alınmıştır.  
  
 Bir mevcut varlık örneği, söz konusu varlığa ilişkin ilk sorgu değiştirmek için özellikleri için gerekli değişiklikleri yapın ve sonra çağrı <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> metodunda <xref:System.Data.Services.Client.DataServiceContext> , gösterildiği gibi bu nesne için bir güncelleştirme göndermek için gereken istemci kitaplığına belirtmek için Aşağıdaki örnekte:  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomerspecific)]
 [!code-vb[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomerspecific)]  
  
 Bir varlık örneğini silmek için çağrı <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metodunda <xref:System.Data.Services.Client.DataServiceContext>, aşağıdaki örnekte gösterildiği gibi:  
  
 [!code-csharp[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproductspecific)]
 [!code-vb[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproductspecific)]  
  
 Daha fazla bilgi için [nasıl yapılır: Ekleme, değiştirme ve silme varlıkları](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md).  
  
## <a name="attaching-entities"></a>Varlık ekleme  
 Bir varlık için bir sorgu çalıştırmadan bir varlığa yüklemeden yaptığınız güncelleştirmeleri kaydetmek istemci kitaplığı sağlayan <xref:System.Data.Services.Client.DataServiceContext>. Kullanım <xref:System.Data.Services.Client.DataServiceContext.AttachTo%2A> belirli bir varlık kümesindeki var olan bir nesne iliştirmek için yöntemi <xref:System.Data.Services.Client.DataServiceContext>. Sonra nesneyi değiştirmek ve veri hizmetine değişiklikleri kaydedin. Aşağıdaki örnekte, değiştirilmiş bir müşteri nesnesi bağlamına bağlı olduğu ve ardından <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> ekli nesnesi olarak işaretlemek için çağrılan <xref:System.Data.Services.Client.EntityStates.Modified> önce <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> çağrılır:  
  
 [!code-csharp[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobjectspecific)]
 [!code-vb[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobjectspecific)]  
  
 Nesneler eklerken aşağıdaki maddeler geçerlidir:  
  
-   Bir nesne bağlı olduğu <xref:System.Data.Services.Client.EntityStates.Unchanged> durumu.  
  
-   Bir nesne eklendiğinde eklenen nesneyi ilgili nesneleri ayrıca bağlı değilsiniz.  
  
-   Varlık zaten bağlam tarafından izleniyorsa, bir nesne eklenemiyor.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.AttachTo%28System.String%2CSystem.Object%2CSystem.String%29> Alan yöntemi aşırı yüklemesini bir `etag` parametresi ile birlikte bir eTag değeri alındı bir varlık nesnesine bağlarken kullanılır. Bu eTag değeri, sonra bağlı nesneyi değişiklikler kaydedildiğinde için eşzamanlılık denetlemek için kullanılır.  
  
 Daha fazla bilgi için [nasıl yapılır: Mevcut bir varlığı Dataservicecontext'e ekleme](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md).  
  
## <a name="creating-and-modifying-relationship-links"></a>Oluşturma ve ilişki bağlantılarını değiştirme  
 Kullanarak yeni bir varlık eklediğinizde <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> yöntemi veya uygun *AddTo* yöntemi <xref:System.Data.Services.Client.DataServiceContext> , sınıf **hizmet Başvurusu Ekle** iletişim oluşturur, ilişkileri Yeni bir varlık ile ilgili varlıklar arasında otomatik olarak tanımlanmamış.  
  
 Oluşturma ve ilişkileri varlık örnekleri arasında değiştirme ve veri hizmeti bu değişiklikleri yansıtmak için istemci kitaplığını sahiptir. Varlıklar arasında ilişkiler modeldeki ilişkileri olarak tanımlanmış ve <xref:System.Data.Services.Client.DataServiceContext> her ilişki bağlamında bir bağlantı nesnesi olarak izler. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Aşağıdaki yöntemleri sağlar <xref:System.Data.Services.Client.DataServiceContext> sınıfı oluşturmak, değiştirmek ve bu bağlantıları silmek için:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A>|İlgili varlık iki nesne arasındaki yeni bir bağlantı oluşturur. Bu yöntemin çağrılması için arama eşdeğer <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> ve <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> hem yeni bir nesne oluşturun ve ilişki varolan bir nesneye tanımlayın.|  
|<xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>|İlgili varlık iki nesne arasındaki yeni bir bağlantı oluşturur.|  
|<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>|İlgili varlık iki nesne arasındaki varolan bağlantıyı güncelleştirir. <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> sıfır veya-bir-bire bir kardinaliteyle bağlantıları silmek için kullanılır (`0..1:1`) ve bire bir (`1:1`). İlgili nesneyi ayarlayarak bunu yapabilirsiniz `null`.|  
|<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A>|Bağlam, silinmek üzere izleme bir bağlantı işaretler, <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılır. İlgili nesneyi silmek ya da önce varolan bir nesneye bağlantı silerek ve ardından yeni bir ilgili nesne için bir bağlantı eklemeyi bir ilişkiyi değiştirmek, bu yöntemi kullanın.|  
|<xref:System.Data.Services.Client.DataServiceContext.AttachLink%2A>|İki varlık nesnesi arasında var olan bir bağlantı bağlamı bildirir. Bu ilişki zaten var data service'taki ve çağırdığınızda bağlantıyı oluşturmak denemez bağlamı varsayar <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi. Nesneler için bir bağlam eklemek ve ikisi arasındaki bağlantıyı da eklemeniz gerekir, bu yöntemi kullanın. Yeni bir ilişki tanımlıyorsanız, bunun yerine kullanmalısınız <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>.|  
|<xref:System.Data.Services.Client.DataServiceContext.DetachLink%2A>|Belirtilen bağlantı bağlamı izlemeyi durdurur. Bu yöntem-çok silmek için kullanılır (`*:*`) ilişkileri. Bire bir kardinalite ile ilişki bağlantıları için bunun yerine kullanmalısınız <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>.|  
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> yeni bir yöntem `Order_Detail` varolan ilgili `Orders` varlık. Çünkü yeni `Order_Details` nesne tarafından izlenen artık <xref:System.Data.Services.Client.DataServiceContext>, eklediğiniz ilişki `Order_Details` varolan nesne `Products` varlık çağırarak tanımlanan <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> yöntemi:  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderspecific)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderspecific)]  
  
 Sırada <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> yöntemi tanımlar bağlamında nesneler yansıtılan bu bağlantıları için veri hizmeti oluşturulması gereken bağlantıları, gezinti özellikleri nesnelerinin kendileri de ayarlamanız gerekir. Önceki örnekte, gezinti özellikleri şu şekilde ayarlamanız gerekir:  
  
 [!code-csharp[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#setnavprops)]
 [!code-vb[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#setnavprops)]  
  
 Daha fazla bilgi için [nasıl yapılır: Veri ilişkileri tanımlama](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md).  
  
## <a name="saving-changes"></a>Değişiklikler kaydediliyor  
 Değişiklikleri izlenir <xref:System.Data.Services.Client.DataServiceContext> örnek ancak sunucuya hemen gönderilmez. Belirtilen bir etkinlik için gerekli değişiklikleri tamamladıktan sonra çağrı <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> veri hizmetine yapılan tüm değişiklikler göndermek için. Daha fazla bilgi için [veri hizmeti bağlamını yönetme](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md). Ayrıca değişiklikleri zaman uyumsuz olarak kullanarak kaydedebilirsiniz <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A> ve <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A> yöntemleri. Daha fazla bilgi için [zaman uyumsuz işlemler](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
- [Zaman Uyumsuz İşlemler](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)
- [Toplu İşlemler](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
- [Nesne Gerçekleştirme](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)
- [Veri Hizmeti Bağlamını Yönetme](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)
