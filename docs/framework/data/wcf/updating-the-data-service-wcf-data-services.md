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
ms.openlocfilehash: 5cf7a6e563069e35a4ac0fe729a616dc1c56bdb5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779748"
---
# <a name="updating-the-data-service-wcf-data-services"></a>Veri hizmeti güncelleştiriliyor (WCF Veri Hizmetleri)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Bir[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akışı kullanmak için istemci kitaplığını kullandığınızda, kitaplık akıştaki girdileri, istemci veri hizmeti sınıflarının örneklerine çevirir. Bu veri hizmeti sınıfları, <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceQuery%601> ait olduğu ile izlenir. İstemci, üzerinde <xref:System.Data.Services.Client.DataServiceContext>yöntemler kullanarak rapor ettiğiniz varlıklara yapılan değişiklikleri izler. Bu yöntemler, istemcinin eklenen ve silinen varlıkları ve ayrıca özellik değerlerinde yaptığınız değişiklikleri ve varlık örnekleri arasındaki ilişkileri izlemesini sağlar. Bu izlenen değişiklikler, <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemini çağırdığınızda REST tabanlı işlemler olarak veri hizmetine geri gönderilir.  
  
> [!NOTE]
> Denetimlerine veri bağlamak <xref:System.Data.Services.Client.DataServiceCollection%601> için bir örneğini kullandığınızda, bağlı denetimdeki verilerde yapılan değişiklikler otomatik olarak <xref:System.Data.Services.Client.DataServiceContext>öğesine bildirilir. Daha fazla bilgi için bkz. [verileri denetimlere bağlama](binding-data-to-controls-wcf-data-services.md).  
  
## <a name="adding-modifying-and-changing-entities"></a>Varlıkları ekleme, değiştirme ve değiştirme  
 Bir[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışa başvuru eklemek için Visual Studio 'da hizmet başvurusu Ekle iletişim kutusunu kullandığınızda, sonuçta elde edilen istemci veri hizmeti sınıflarının her biri null yapılamayan varlık özelliği için bir parametre alan statik bir *oluşturma* yöntemine sahiptir . Aşağıdaki örnekte olduğu gibi, varlık türü sınıflarının örneklerini oluşturmak için bu yöntemi kullanabilirsiniz:  
  
 [!code-csharp[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#createnewproduct)]
 [!code-vb[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#createnewproduct)]  
  
 Bir varlık örneği eklemek için, aşağıdaki örnekte olduğu gibi **hizmet başvurusu Ekle** iletişim kutusu tarafından <xref:System.Data.Services.Client.DataServiceContext> oluşturulan sınıfta uygun *AddTo* metodunu çağırın:  
  
 [!code-csharp[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproductspecific)]
 [!code-vb[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproductspecific)]  
  
 Bu, nesnesini bağlamına ve doğru varlık kümesine ekler. Ayrıca çağırabilirsiniz <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>, ancak bunun yerine varlık kümesi adını belirtmeniz gerekir. Eklenen varlığın başka varlıklarla bir veya daha fazla ilişkisi varsa, <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> yöntemini kullanabilir veya önceki yöntemlerden birini kullanabilir ve ayrıca bu bağlantıları açıkça tanımlayabilirsiniz. Bu işlemler, bu konunun ilerleyen kısımlarında ele alınmıştır.  
  
 Var olan bir varlık örneğini değiştirmek için, bu varlık için ilk sorgu yapın, özelliklerinde istediğiniz değişiklikleri yapın ve ardından, <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> <xref:System.Data.Services.Client.DataServiceContext> istemci kitaplığına bu nesne için bir güncelleştirme gönderilmesi gerektiğini belirtmek için ' de gösterildiği gibi bu yöntemi çağırın. Aşağıdaki örnek:  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomerspecific)]
 [!code-vb[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomerspecific)]  
  
 Bir varlık örneğini silmek için, aşağıdaki örnekte <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> gösterildiği gibi yöntemini <xref:System.Data.Services.Client.DataServiceContext>üzerinde çağırın:  
  
 [!code-csharp[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproductspecific)]
 [!code-vb[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproductspecific)]  
  
 Daha fazla bilgi için [nasıl yapılır: Varlık](how-to-add-modify-and-delete-entities-wcf-data-services.md)ekleyin, değiştirin ve silin.  
  
## <a name="attaching-entities"></a>Varlıkları iliştirme  
 İstemci kitaplığı, varlığı yüklemek <xref:System.Data.Services.Client.DataServiceContext>için önce bir sorgu yürütmeden bir varlığa yaptığınız güncelleştirmeleri kaydetmenizi sağlar. İçindeki belirli bir varlık kümesine varolan bir nesneyi iliştirmek için <xref:System.Data.Services.Client.DataServiceContext.AttachTo%2A> yöntemini kullanın <xref:System.Data.Services.Client.DataServiceContext>. Daha sonra nesneyi değiştirebilir ve değişiklikleri veri hizmetine kaydedebilirsiniz. Aşağıdaki örnekte, bir adlı bir müşteri nesnesi bağlamına iliştirilir ve daha sonra <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> eklenmiş <xref:System.Data.Services.Client.EntityStates.Modified> nesneyi çağrılmadan önce <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> işaretlemek için çağırılır:  
  
 [!code-csharp[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobjectspecific)]
 [!code-vb[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobjectspecific)]  
  
 Nesneleri iliştirirken aşağıdaki noktalar geçerlidir:  
  
- <xref:System.Data.Services.Client.EntityStates.Unchanged> Duruma bir nesne eklenir.  
  
- Bir nesne eklendiğinde, eklenen nesneyle ilgili nesneler de eklenmez.  
  
- Varlık bağlam tarafından zaten izleniyorsa bir nesne iliştirilemez.  
  
- <xref:System.Data.Services.Client.DataServiceContext.AttachTo%28System.String%2CSystem.Object%2CSystem.String%29> Bir`etag` parametre alan aşırı yükleme, bir ETag değeriyle birlikte alınan bir varlık nesnesini iliştirirken kullanılır. Bu eTag değeri, eklenen nesnede değişiklik yapıldığında eşzamanlılık denetlemek için kullanılır.  
  
 Daha fazla bilgi için [nasıl yapılır: DataServiceContext](attach-an-existing-entity-to-dc-wcf-data.md)'e mevcut bir varlık ekleyin.  
  
## <a name="creating-and-modifying-relationship-links"></a>Ilişki bağlantıları oluşturma ve değiştirme  
 <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> **Hizmet başvurusu Ekle** iletişim kutusunun oluşturduğu <xref:System.Data.Services.Client.DataServiceContext> sınıfın yöntemini veya uygun *AddTo* yöntemini kullanarak yeni bir varlık eklediğinizde, yeni varlık ve ilgili varlıklar arasındaki ilişkiler otomatik olarak tanımlanmadı.  
  
 Varlık örnekleri arasında ilişkiler oluşturabilir ve değiştirebilir ve istemci kitaplığının veri hizmetindeki değişiklikleri yansıtmasını sağlayabilirsiniz. Varlıklar arasındaki ilişkiler modelde ilişkiler olarak tanımlanır ve <xref:System.Data.Services.Client.DataServiceContext> her ilişkiyi bağlamdaki bir bağlantı nesnesi olarak izler. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Bu bağlantıları oluşturmak, değiştirmek ve <xref:System.Data.Services.Client.DataServiceContext> silmek için sınıfında aşağıdaki yöntemleri sağlar:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A>|İki ilgili varlık nesnesi arasında yeni bir bağlantı oluşturur. Bu yöntemi çağırmak, <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> her ikisi de yeni nesneyi oluşturmak ve var olan bir nesneyle ilişkiyi tanımlamak için çağırır.|  
|<xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>|İki ilgili varlık nesnesi arasında yeni bir bağlantı oluşturur.|  
|<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>|İki ilgili varlık nesnesi arasında varolan bir bağlantıyı güncelleştirir. <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>, sıfır ya da-bire-bir (`0..1:1`) ve bire bir (`1:1`) kardinalitesiyle bağlantıları silmek için de kullanılır. Bunu, ilgili nesnesini olarak `null`ayarlayarak yapabilirsiniz.|  
|<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A>|<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> Yöntem çağrıldığında bağlamın silinmek üzere izlemesiyle bir bağlantı işaretler. İlgili bir nesneyi sildiğinizde veya bir ilişkiyi değiştirirken, önce mevcut bir nesnenin bağlantısını silerek ve sonra yeni ilgili nesneye bir bağlantı ekleyerek bu yöntemi kullanın.|  
|<xref:System.Data.Services.Client.DataServiceContext.AttachLink%2A>|İki varlık nesnesi arasında var olan bir bağlantının bağlamına bildirir. Bağlam, bu ilişkinin veri hizmetinde zaten bulunduğunu varsayar ve <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemini çağırdığınızda bağlantıyı oluşturmayı denemez. Bir içeriğe nesne iliştirmeye ve ayrıca iki arasındaki bağlantıyı iliştirmeye ihtiyaç duyduğunuzda bu yöntemi kullanın. Yeni bir ilişki tanımlıyorsanız, bunun yerine kullanmanız <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>gerekir.|  
|<xref:System.Data.Services.Client.DataServiceContext.DetachLink%2A>|Bağlamda belirtilen bağlantıyı izlemeyi durduruyor. Bu yöntem, bire çok (`*:*`) ilişkilerini silmek için kullanılır. Bir kardinalitesiyle ilişki bağlantıları için, bunun yerine kullanmanız <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>gerekir.|  
  
 Aşağıdaki örnek, var <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> `Orders` olan bir varlıkla ilgili yeni `Order_Detail` bir eklemek için yönteminin nasıl kullanılacağını gösterir. Yeni `Order_Details` nesne artık <xref:System.Data.Services.Client.DataServiceContext>tarafından izlendiğinden, eklenen `Order_Details` nesnenin mevcut varlığa olan `Products` ilişkisi <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> yöntemi çağırarak tanımlanmıştır:  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderspecific)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderspecific)]  
  
 <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> Yöntemi, veri hizmetinde oluşturulması gereken bağlantıları tanımlasa da, bu bağlantıların bağlamdaki nesnelere yansıtılmasını sağlamak için nesneler üzerinde gezinti özelliklerini de ayarlamanız gerekir. Önceki örnekte, gezinti özelliklerini aşağıdaki şekilde ayarlamanız gerekir:  
  
 [!code-csharp[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#setnavprops)]
 [!code-vb[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#setnavprops)]  
  
 Daha fazla bilgi için [nasıl yapılır: Varlık Ilişkilerini](how-to-define-entity-relationships-wcf-data-services.md)tanımlayın.  
  
## <a name="saving-changes"></a>Değişiklikler kaydediliyor  
 Değişiklikler <xref:System.Data.Services.Client.DataServiceContext> örnekte izlenir, ancak anında sunucuya gönderilmez. Belirtilen bir etkinlik için gerekli değişikliklerle işiniz bittiğinde, tüm değişiklikleri veri hizmetine göndermek <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> için çağırın. Daha fazla bilgi için bkz. [veri hizmeti bağlamını yönetme](managing-the-data-service-context-wcf-data-services.md). Ayrıca, <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A> ve <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A> yöntemlerini kullanarak değişiklikleri zaman uyumsuz olarak kaydedebilirsiniz. Daha fazla bilgi için bkz. [zaman uyumsuz işlemler](asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
- [Zaman Uyumsuz İşlemler](asynchronous-operations-wcf-data-services.md)
- [Toplu İşlemler](batching-operations-wcf-data-services.md)
- [Nesne Gerçekleştirme](object-materialization-wcf-data-services.md)
- [Veri Hizmeti Bağlamını Yönetme](managing-the-data-service-context-wcf-data-services.md)
