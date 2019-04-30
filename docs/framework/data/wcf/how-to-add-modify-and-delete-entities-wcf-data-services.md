---
title: 'Nasıl yapılır: Ekleme, değiştirme ve (WCF Veri Hizmetleri) varlıklarını silme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
ms.openlocfilehash: 66f115bf3bf51b4b5612240c4e34eaf9e08bec0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765563"
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Nasıl yapılır: Ekleme, değiştirme ve (WCF Veri Hizmetleri) varlıklarını silme
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplıkları, oluşturabilir, güncelleştirme ve nesnelerde eşdeğer eylemleri gerçekleştirerek varlık verilerini bir veri hizmeti silme <xref:System.Data.Services.Client.DataServiceContext>. Daha fazla bilgi için [veri hizmetini güncelleştirme](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulan istemci veri hizmeti sınıfları kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir nesne örneği oluşturur ve <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> metodunda <xref:System.Data.Services.Client.DataServiceContext> bağlamında öğesi oluşturmak için. Veriler için bir HTTP POST iletisi gönderilir ne zaman hizmet <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılır.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek alır ve var olan bir nesneyi değiştirir ve ardından çağırır <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> metodunda <xref:System.Data.Services.Client.DataServiceContext> öğe bağlamında güncelleştirilmiş olarak işaretleyebilirsiniz. Verileri birleştirme HTTP iletisi gönderilir ne zaman hizmet <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılır.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çağrıları <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metodunda <xref:System.Data.Services.Client.DataServiceContext> öğe bağlamında silindi olarak işaretlemek için. Veriler için bir HTTP DELETE iletisi gönderilir ne zaman hizmet <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılır.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir nesne örneği oluşturur ve <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metodunda <xref:System.Data.Services.Client.DataServiceContext> ilgili sipariş bağlantısını birlikte bağlamında öğesi oluşturmak için. Veriler için bir HTTP POST iletisi gönderilir ne zaman hizmet <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılır.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Nasıl yapılır: Mevcut bir varlığı Dataservicecontext'e ekleme](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md)
- [Nasıl yapılır: Veri ilişkileri tanımlama](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md)
- [Toplu İşlemler](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
