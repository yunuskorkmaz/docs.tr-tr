---
title: "Veri Hizmeti (WCF Veri Hizmetleri) güncelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
- WCF Data Services, client library
ms.assetid: 00d993be-ffed-4dea-baf7-6eea982cdb54
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc8041dee12c8300e18e6321c717cbd80b93d650
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="updating-the-data-service-wcf-data-services"></a>Veri Hizmeti (WCF Veri Hizmetleri) güncelleştirme
Kullandığınızda [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kullanmak için istemci kitaplığı bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış, kitaplık istemci veri hizmeti sınıfların örneklerini akışa girdileri çevirir. Bu veri hizmeti sınıflarını kullanarak izlenen <xref:System.Data.Services.Client.DataServiceContext> hangi <xref:System.Data.Services.Client.DataServiceQuery%601> ait. İstemci üzerinde yöntemleri kullanarak rapor varlıklara değişiklikleri izleyen <xref:System.Data.Services.Client.DataServiceContext>. Bu yöntemler, eklenen ve Silinen varlıkları ve ayrıca özellik değerleri veya varlık örnekleri arasında ilişkiler için yaptığınız değişiklikleri izlemek istemci etkinleştirin. Çağırdığınızda bu izlenen değişiklikleri REST tabanlı işlemler veri hizmetine gönderilen <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi.  
  
> [!NOTE]
>  Bir örneğini kullandığınızda <xref:System.Data.Services.Client.DataServiceCollection%601> verileri denetimlere bağlamak için ilişkili denetim verilerde yapılan değişiklikleri otomatik olarak bildirilen <xref:System.Data.Services.Client.DataServiceContext>. Daha fazla bilgi için bkz: [denetimlere veri bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
## <a name="adding-modifying-and-changing-entities"></a>Ekleme, değiştirme ve varlıkları değiştirme  
 Kullandığınızda **hizmet Başvurusu Ekle** iletişim için bir başvuru eklemek için Visual Studio'da bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış, sonuçta elde edilen istemci veri hizmeti sınıflarını her bir statik sahip *oluşturma* alır yöntemi Her bir null varlık özellik için bir parametre. Varlık örneklerini aşağıdaki örnekteki gibi türü sınıfları oluşturmak için bu yöntemi kullanabilirsiniz:  
  
 [!code-csharp[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#createnewproduct)]
 [!code-vb[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#createnewproduct)]  
  
 Bir varlık örneği eklemek için uygun çağrı *AddTo* yöntemi <xref:System.Data.Services.Client.DataServiceContext> tarafından oluşturulan sınıf **hizmet Başvurusu Ekle** iletişim kutusunda, aşağıdaki örnekteki gibi:  
  
 [!code-csharp[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproductspecific)]
 [!code-vb[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproductspecific)]  
  
 Bu nesne bağlamı ve doğru varlık kümesini içine ekler. Ayrıca, çağırabilirsiniz <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>, ancak bunun yerine varlık kümesi adı sağlamanız gerekir. Eklenen varlık diğer varlıklar için bir veya daha fazla ilişkileri varsa, kullanabilir <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> yöntemi önceki yöntemlerden birini kullanın veya bu bağlantıları da açıkça tanımlayın. Bu işlemler bu konunun ilerleyen bölümlerinde ele alınmıştır.  
  
 Var olan varlık örneği, bu varlık için ilk sorgu değiştirmek için özellikleri için istediğiniz değişiklikleri yapın ve ardından çağıran <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext> , gösterildiği gibi bu nesne için bir güncelleştirme göndermek için gereken istemci kitaplığına belirtmek için Aşağıdaki örnek:  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomerspecific)]
 [!code-vb[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomerspecific)]  
  
 Bir varlık örneği silmek için arama <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext>, aşağıdaki örnekte gösterildiği gibi:  
  
 [!code-csharp[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproductspecific)]
 [!code-vb[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproductspecific)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: ekleme, değiştirme ve silme varlıklar](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md).  
  
## <a name="attaching-entities"></a>Varlıklar ekleme  
 Bir varlık için bir sorgu çalıştırmadan varlık kümesine yüklemek için yaptığınız güncelleştirmeleri kaydetmek istemci kitaplığı sağlayan <xref:System.Data.Services.Client.DataServiceContext>. Kullanım <xref:System.Data.Services.Client.DataServiceContext.AttachTo%2A> kümesinde belirli bir varlık için varolan bir nesne eklemek için yöntemi <xref:System.Data.Services.Client.DataServiceContext>. Nesneyi değiştirmek ve veri hizmeti değişiklikleri kaydedin. Aşağıdaki örnekte, değiştirilmiş bir müşteri nesnesi bağlamına bağlı olduğu ve ardından <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> ekli nesnesi olarak işaretlemek için adlı <xref:System.Data.Services.Client.EntityStates.Modified> önce <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> adı verilir:  
  
 [!code-csharp[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobjectspecific)]
 [!code-vb[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobjectspecific)]  
  
 Nesneleri eklerken aşağıdaki maddeler geçerlidir:  
  
-   Bir nesne, bağlı olduğu <xref:System.Data.Services.Client.EntityStates.Unchanged> durumu.  
  
-   Bir nesne iliştirildiğinde ekli nesneyle ilişkili nesnelerin de bağlanmış değilsiniz.  
  
-   Varlık kapsamında zaten izleniyorsa bir nesne eklenemiyor.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.AttachTo%28System.String%2CSystem.Object%2CSystem.String%29> Geçen yöntemi aşırı yüklemesini bir `etag` parametresi ile birlikte bir eTag değeri alındı bir varlık nesnesine taktığınızda kullanılır. Bu eTag değeri sonra ekli nesnedeki değişiklikler kaydedildiğinde eşzamanlılık denetlemek için kullanılır.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: varolan bir varlık için DataServiceContext eklemek](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md).  
  
## <a name="creating-and-modifying-relationship-links"></a>Oluşturma ve ilişki bağlantıları değiştirme  
 Kullanarak yeni bir varlık eklediğinizde <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> yöntemi veya uygun *AddTo* yöntemi <xref:System.Data.Services.Client.DataServiceContext> , sınıf **hizmet Başvurusu Ekle** iletişim oluşturur, herhangi bir ilişki Yeni varlık ile ilgili varlıklar arasında otomatik olarak tanımlanmamış.  
  
 Oluşturma ve varlık örnekleri arasındaki ilişkileri değiştirmek ve veri hizmeti bu değişiklikleri yansıtmak için istemci kitaplığı sahiptir. Varlıklar arasındaki ilişkiler modelinde ilişkileri olarak tanımlanmış ve <xref:System.Data.Services.Client.DataServiceContext> her ilişki bağlamında bir bağlantı nesnesi olarak izler. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Aşağıdaki yöntemleri sağlar <xref:System.Data.Services.Client.DataServiceContext> sınıfı oluşturmak, değiştirmek ve bu bağlantıları silmek için:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A>|İki ilgili varlık nesneler arasındaki yeni bir bağlantı oluşturur. Bu yöntemin çağrılması için arama eşdeğer <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> ve <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> hem yeni nesnesi oluşturmanız ve varolan bir nesneye ilişki tanımlamak için.|  
|<xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>|İki ilgili varlık nesneler arasındaki yeni bir bağlantı oluşturur.|  
|<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>|Varolan bir bağlantıyı iki ilgili varlık nesneler arasındaki güncelleştirir. <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>Ayrıca bağlantıları sıfır-veya---bire bir önem düzeyi ile silmek için kullanılır (`0..1:1`) ve bire (`1:1`). İlgili nesne ayarlayarak bunu yapabilirsiniz `null`.|  
|<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A>|Bağlam silme işlemi için izleme bir bağlantı işaretler zaman <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılır. Bir ilişkili nesne silme veya önce var olan bir nesne bağlantısını silme ve ardından yeni ilgili nesne için bir bağlantı ekleyerek bir ilişki değiştirdiğinizde, bu yöntemi kullanın.|  
|<xref:System.Data.Services.Client.DataServiceContext.AttachLink%2A>|İki varlık nesnesi arasındaki varolan bağlantıyı bağlamını uyarır. Bu ilişki zaten veri hizmeti var ve çağırdığınızda bağlantıyı oluşturmak denemez bağlam varsayar <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi. Bir bağlam nesneleri eklemek ve de iki arasındaki bağlantı ekleyebilirsiniz gerektiğinde bu yöntemi kullanın. Yeni bir ilişki tanımlıyorsanız, kullanmanız <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>.|  
|<xref:System.Data.Services.Client.DataServiceContext.DetachLink%2A>|Belirtilen bağlantı bağlamında izlemeyi durdurur. Bu yöntem bir çok silmek için kullanılır (`*:*`) ilişkiler. Bir önem düzeyi ile ilişki bağlantıları için bunun yerine kullanmanız gerekir <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>.|  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> yeni bir ekleme yöntemi `Order_Detail` var olan ilgili `Orders` varlık. Çünkü yeni `Order_Details` nesnesi tarafından izlenen şimdi <xref:System.Data.Services.Client.DataServiceContext>, eklenen ilişkisi `Order_Details` varolan nesne `Products` varlık çağırarak tanımlanmış <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> yöntemi:  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderspecific)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderspecific)]  
  
 Sırada <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> yöntemi tanımlar bağlamda nesneleri yansıtılan bu bağlantıları sağlamak için veri hizmeti oluşturulmalıdır bağlantılar, gezinti özellikleri nesnelerinin kendileri de ayarlamanız gerekir. Önceki örnekte, gezinti özellikleri şu şekilde ayarlamanız gerekir:  
  
 [!code-csharp[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#setnavprops)]
 [!code-vb[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#setnavprops)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: varlık ilişkileri tanımlamak](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md).  
  
## <a name="saving-changes"></a>Değişiklikler kaydediliyor  
 Değişiklikleri izlenir <xref:System.Data.Services.Client.DataServiceContext> örnek ancak sunucuya hemen gönderilmez. Belirtilen bir etkinlik için gerekli değişiklikleri tamamladıktan sonra arama <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> veri hizmeti yapılan tüm değişiklikler göndermek için. Daha fazla bilgi için bkz: [veri Hizmet bağlamı yönetme](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md). Ayrıca değişiklikleri zaman uyumsuz olarak kullanarak kaydedebilirsiniz <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A> ve <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A> yöntemleri. Daha fazla bilgi için bkz: [zaman uyumsuz işlemleri](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [Zaman Uyumsuz İşlemler](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 [Toplu İşlemler](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 [Nesne Gerçekleştirme](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
 [Veri Hizmeti Bağlamını Yönetme](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)
