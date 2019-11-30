---
title: 'Nasıl yapılır: varlıkları ekleme, değiştirme ve silme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
ms.openlocfilehash: 501bec59a61b51ec4bece4b0ce2f941189b35ed0
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569193"
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Nasıl yapılır: varlıkları ekleme, değiştirme ve silme (WCF Veri Hizmetleri)
WCF Veri Hizmetleri istemci kitaplıkları ile, bir veri hizmetinde varlık verilerini oluşturabilir, güncelleştirebilir ve silebilirsiniz <xref:System.Data.Services.Client.DataServiceContext>nesneler üzerinde eşdeğer eylemler gerçekleştirerek. Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir nesne örneği oluşturur ve sonra bağlamı oluşturmak için <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> yöntemini çağırır. <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrıldığında veri hizmetine bir HTTP POST iletisi gönderilir.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, var olan bir nesneyi alır ve değiştirir ve ardından bağlamdaki öğeyi güncelleştirilmiş olarak işaretlemek için <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> yöntemini çağırır. <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrıldığında veri hizmetine HTTP BIRLEŞTIRME iletisi gönderilir.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bağlamındaki öğeyi silinmiş olarak işaretlemek için <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> yöntemini çağırır. <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrıldığında veri hizmetine HTTP DELETE iletisi gönderilir.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yeni bir nesne örneği oluşturur ve sonra, öğeyi bağlamda oluşturmak için <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> yöntemini çağırarak ilgili siparişin bağlantısı ile birlikte. <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrıldığında veri hizmetine bir HTTP POST iletisi gönderilir.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Nasıl yapılır: Mevcut Bir Varlığı DataServiceContext’e Ekleme](attach-an-existing-entity-to-dc-wcf-data.md)
- [Nasıl yapılır: Veri İlişkileri Tanımlama](how-to-define-entity-relationships-wcf-data-services.md)
- [Toplu İşlemler](batching-operations-wcf-data-services.md)
