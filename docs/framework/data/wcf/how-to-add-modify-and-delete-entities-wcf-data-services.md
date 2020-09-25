---
title: 'Nasıl yapılır: varlıkları ekleme, değiştirme ve silme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
ms.openlocfilehash: 3d147f05e2911cdaa05c5fc2374e14c539235fda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172534"
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Nasıl yapılır: varlıkları ekleme, değiştirme ve silme (WCF Veri Hizmetleri)

WCF Veri Hizmetleri istemci kitaplıkları ile, içindeki nesneler üzerinde eşdeğer eylemler gerçekleştirerek bir veri hizmetinde varlık verileri oluşturabilir, güncelleştirebilir ve silebilirsiniz <xref:System.Data.Services.Client.DataServiceContext> . Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, yeni bir nesne örneği oluşturur ve sonra <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> <xref:System.Data.Services.Client.DataServiceContext> öğesini bağlamda oluşturmak için üzerinde yöntemini çağırır. Yöntemi çağrıldığında veri hizmetine bir HTTP POST iletisi gönderilir <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> .  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, var olan bir nesneyi alır ve değiştirir ve sonra <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> <xref:System.Data.Services.Client.DataServiceContext> öğesini bağlamındaki öğesini güncelleştirilmiş olarak işaretlemek için üzerinde yöntemini çağırır. Yöntemi çağrıldığında veri hizmetine bir HTTP BIRLEŞTIRME iletisi gönderilir <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> .  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> , <xref:System.Data.Services.Client.DataServiceContext> öğesini bağlamdaki öğeyi silinmiş olarak işaretlemek için üzerinde yöntemini çağırır. Bir HTTP DELETE iletisi, yöntem çağrıldığında veri hizmetine gönderilir <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> .  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, yeni bir nesne örneği oluşturur ve sonra <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> <xref:System.Data.Services.Client.DataServiceContext> öğesini bağlamda, ilişkili siparişin bağlantısıyla birlikte oluşturmak için üzerinde yöntemini çağırır. Yöntemi çağrıldığında veri hizmetine bir HTTP POST iletisi gönderilir <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> .  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Nasıl yapılır: Mevcut Bir Varlığı DataServiceContext’e Ekleme](attach-an-existing-entity-to-dc-wcf-data.md)
- [Nasıl yapılır: Veri İlişkileri Tanımlama](how-to-define-entity-relationships-wcf-data-services.md)
- [Toplu İşlemler](batching-operations-wcf-data-services.md)
