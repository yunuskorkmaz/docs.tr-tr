---
title: Veri hizmeti güncelleştiriliyor (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
- WCF Data Services, client library
ms.assetid: 00d993be-ffed-4dea-baf7-6eea982cdb54
ms.openlocfilehash: 3e2bd3f4ca5402abe4a7f8ec8f5410effaee6700
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180614"
---
# <a name="updating-the-data-service-wcf-data-services"></a>Veri hizmeti güncelleştiriliyor (WCF Veri Hizmetleri)

Açık Veri Protokolü (OData) akışını kullanmak için WCF Veri Hizmetleri istemci kitaplığını kullandığınızda, kitaplık akıştaki girdileri istemci veri hizmeti sınıflarının örneklerine çevirir. Bu veri hizmeti sınıfları, ait olduğu ile izlenir <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceQuery%601> . İstemci, üzerinde yöntemler kullanarak rapor ettiğiniz varlıklara yapılan değişiklikleri izler <xref:System.Data.Services.Client.DataServiceContext> . Bu yöntemler, istemcinin eklenen ve silinen varlıkları ve ayrıca özellik değerlerinde yaptığınız değişiklikleri ve varlık örnekleri arasındaki ilişkileri izlemesini sağlar. Bu izlenen değişiklikler, yöntemini çağırdığınızda REST tabanlı işlemler olarak veri hizmetine geri gönderilir <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> .  
  
> [!NOTE]
> <xref:System.Data.Services.Client.DataServiceCollection%601>Denetimlerine veri bağlamak için bir örneğini kullandığınızda, bağlı denetimdeki verilerde yapılan değişiklikler otomatik olarak öğesine bildirilir <xref:System.Data.Services.Client.DataServiceContext> . Daha fazla bilgi için bkz. [verileri denetimlere bağlama](binding-data-to-controls-wcf-data-services.md).  
  
## <a name="adding-modifying-and-changing-entities"></a>Varlıkları ekleme, değiştirme ve değiştirme  

 Bir OData akışına başvuru eklemek için Visual Studio 'da **hizmet başvurusu Ekle** iletişim kutusunu kullandığınızda, sonuçta elde edilen istemci veri hizmeti sınıflarının her biri null yapılamayan varlık özelliği için bir parametre alan statik bir *oluşturma* yöntemine sahiptir. Aşağıdaki örnekte olduğu gibi, varlık türü sınıflarının örneklerini oluşturmak için bu yöntemi kullanabilirsiniz:  
  
 [!code-csharp[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#createnewproduct)]
 [!code-vb[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#createnewproduct)]  
  
 Bir varlık örneği eklemek için, *AddTo* <xref:System.Data.Services.Client.DataServiceContext> Aşağıdaki örnekte olduğu gibi **hizmet başvurusu Ekle** iletişim kutusu tarafından oluşturulan sınıfta uygun AddTo metodunu çağırın:  
  
 [!code-csharp[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproductspecific)]
 [!code-vb[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproductspecific)]  
  
 Bu, nesnesini bağlamına ve doğru varlık kümesine ekler. Ayrıca çağırabilirsiniz <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> , ancak bunun yerine varlık kümesi adını belirtmeniz gerekir. Eklenen varlığın başka varlıklarla bir veya daha fazla ilişkisi varsa, <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> yöntemini kullanabilir veya önceki yöntemlerden birini kullanabilir ve ayrıca bu bağlantıları açıkça tanımlayabilirsiniz. Bu işlemler, bu konunun ilerleyen kısımlarında ele alınmıştır.  
  
 Mevcut bir varlık örneğini değiştirmek için, bu varlık için ilk sorgu yapın, özelliklerinde istediğiniz değişiklikleri yapın ve ardından <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> , <xref:System.Data.Services.Client.DataServiceContext> Aşağıdaki örnekte gösterildiği gibi, istemci kitaplığına bu nesne için bir güncelleştirme gönderilmesi gerektiğini belirtmek için ' daki yöntemi çağırın:  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomerspecific)]
 [!code-vb[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomerspecific)]  
  
 Bir varlık örneğini silmek için, <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> <xref:System.Data.Services.Client.DataServiceContext> Aşağıdaki örnekte gösterildiği gibi yöntemini üzerinde çağırın:  
  
 [!code-csharp[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproductspecific)]
 [!code-vb[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproductspecific)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: varlıkları ekleme, değiştirme ve silme](how-to-add-modify-and-delete-entities-wcf-data-services.md).  
  
## <a name="attaching-entities"></a>Varlıkları iliştirme  

 İstemci kitaplığı, varlığı yüklemek için önce bir sorgu yürütmeden bir varlığa yaptığınız güncelleştirmeleri kaydetmenizi sağlar <xref:System.Data.Services.Client.DataServiceContext> . <xref:System.Data.Services.Client.DataServiceContext.AttachTo%2A>İçindeki belirli bir varlık kümesine varolan bir nesneyi iliştirmek için yöntemini kullanın <xref:System.Data.Services.Client.DataServiceContext> . Daha sonra nesneyi değiştirebilir ve değişiklikleri veri hizmetine kaydedebilirsiniz. Aşağıdaki örnekte, bir adlı bir müşteri nesnesi bağlamına iliştirilir ve daha sonra <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> eklenmiş nesneyi <xref:System.Data.Services.Client.EntityStates.Modified> çağrılmadan önce işaretlemek için çağırılır <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> :  
  
 [!code-csharp[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobjectspecific)]
 [!code-vb[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobjectspecific)]  
  
 Nesneleri iliştirirken aşağıdaki noktalar geçerlidir:  
  
- Duruma bir nesne eklenir <xref:System.Data.Services.Client.EntityStates.Unchanged> .  
  
- Bir nesne eklendiğinde, eklenen nesneyle ilgili nesneler de eklenmez.  
  
- Varlık bağlam tarafından zaten izleniyorsa bir nesne iliştirilemez.  
  
- <xref:System.Data.Services.Client.DataServiceContext.AttachTo%28System.String%2CSystem.Object%2CSystem.String%29>Bir parametre alan aşırı yükleme, `etag` bir ETag değeriyle birlikte alınan bir varlık nesnesini iliştirirken kullanılır. Bu eTag değeri, eklenen nesnede değişiklik yapıldığında eşzamanlılık denetlemek için kullanılır.  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: mevcut varlığı DataServiceContext 'e iliştirme](attach-an-existing-entity-to-dc-wcf-data.md).  
  
## <a name="creating-and-modifying-relationship-links"></a>Ilişki bağlantıları oluşturma ve değiştirme  

 <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>Hizmet başvurusu Ekle iletişim kutusunun oluşturduğu sınıfın yöntemini veya uygun *AddTo* yöntemini kullanarak yeni bir varlık eklediğinizde <xref:System.Data.Services.Client.DataServiceContext> , yeni varlık ve ilgili varlıklar **Add Service Reference** arasındaki ilişkiler otomatik olarak tanımlanmamıştır.  
  
 Varlık örnekleri arasında ilişkiler oluşturabilir ve değiştirebilir ve istemci kitaplığının veri hizmetindeki değişiklikleri yansıtmasını sağlayabilirsiniz. Varlıklar arasındaki ilişkiler modelde ilişkiler olarak tanımlanır ve <xref:System.Data.Services.Client.DataServiceContext> her ilişkiyi bağlamdaki bir bağlantı nesnesi olarak izler. WCF Veri Hizmetleri <xref:System.Data.Services.Client.DataServiceContext> Bu bağlantıları oluşturmak, değiştirmek ve silmek için sınıfında aşağıdaki yöntemleri sağlar:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A>|İki ilgili varlık nesnesi arasında yeni bir bağlantı oluşturur. Bu yöntemi çağırmak, <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> her ikisi de yeni nesneyi oluşturmak ve var olan bir nesneyle ilişkiyi tanımlamak için çağırır.|  
|<xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>|İki ilgili varlık nesnesi arasında yeni bir bağlantı oluşturur.|  
|<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>|İki ilgili varlık nesnesi arasında varolan bir bağlantıyı güncelleştirir. <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> , sıfır ya da-bire-bir ( `0..1:1` ) ve bire bir () kardinalitesiyle bağlantıları silmek için de kullanılır `1:1` . Bunu, ilgili nesnesini olarak ayarlayarak yapabilirsiniz `null` .|  
|<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A>|Yöntem çağrıldığında bağlamın silinmek üzere izlemesiyle bir bağlantı işaretler <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> . İlgili bir nesneyi sildiğinizde veya bir ilişkiyi değiştirirken, önce mevcut bir nesnenin bağlantısını silerek ve sonra yeni ilgili nesneye bir bağlantı ekleyerek bu yöntemi kullanın.|  
|<xref:System.Data.Services.Client.DataServiceContext.AttachLink%2A>|İki varlık nesnesi arasında var olan bir bağlantının bağlamına bildirir. Bağlam, bu ilişkinin veri hizmetinde zaten bulunduğunu varsayar ve yöntemini çağırdığınızda bağlantıyı oluşturmayı denemez <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> . Bir içeriğe nesne iliştirmeye ve ayrıca iki arasındaki bağlantıyı iliştirmeye ihtiyaç duyduğunuzda bu yöntemi kullanın. Yeni bir ilişki tanımlıyorsanız, bunun yerine kullanmanız gerekir <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> .|  
|<xref:System.Data.Services.Client.DataServiceContext.DetachLink%2A>|Bağlamda belirtilen bağlantıyı izlemeyi durduruyor. Bu yöntem, bire çok () ilişkilerini silmek için kullanılır `*:*` . Bir kardinalitesiyle ilişki bağlantıları için, bunun yerine kullanmanız gerekir <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> .|  
  
 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> `Order_Detail` var olan bir varlıkla ilgili yeni bir eklemek için yönteminin nasıl kullanılacağını gösterir `Orders` . Yeni `Order_Details` nesne artık tarafından izlendiğinden <xref:System.Data.Services.Client.DataServiceContext> , eklenen `Order_Details` nesnenin mevcut varlığa olan ilişkisi `Products` yöntemi çağırarak tanımlanmıştır <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> :  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderspecific)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderspecific)]  
  
 Yöntemi, <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> veri hizmetinde oluşturulması gereken bağlantıları tanımlasa da, bu bağlantıların bağlamdaki nesnelere yansıtılmasını sağlamak için nesneler üzerinde gezinti özelliklerini de ayarlamanız gerekir. Önceki örnekte, gezinti özelliklerini aşağıdaki şekilde ayarlamanız gerekir:  
  
 [!code-csharp[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#setnavprops)]
 [!code-vb[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#setnavprops)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: varlık Ilişkilerini tanımlama](how-to-define-entity-relationships-wcf-data-services.md).  
  
## <a name="saving-changes"></a>Değişiklikler kaydediliyor  

 Değişiklikler örnekte izlenir, <xref:System.Data.Services.Client.DataServiceContext> ancak anında sunucuya gönderilmez. Belirtilen bir etkinlik için gerekli değişikliklerle işiniz bittiğinde, <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> tüm değişiklikleri veri hizmetine göndermek için çağırın. Daha fazla bilgi için bkz. [veri hizmeti bağlamını yönetme](managing-the-data-service-context-wcf-data-services.md). Ayrıca, ve yöntemlerini kullanarak değişiklikleri zaman uyumsuz olarak <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A> kaydedebilirsiniz <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A> . Daha fazla bilgi için bkz. [zaman uyumsuz işlemler](asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
- [Zaman Uyumsuz İşlemler](asynchronous-operations-wcf-data-services.md)
- [Toplu İşlemler](batching-operations-wcf-data-services.md)
- [Nesne Gerçekleştirme](object-materialization-wcf-data-services.md)
- [Veri Hizmeti Bağlamını Yönetme](managing-the-data-service-context-wcf-data-services.md)
