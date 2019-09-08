---
title: 'Nasıl yapılır: Varlık ekleme, değiştirme ve silme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
ms.openlocfilehash: 13c59bee9fc58dbe8c5b8c768fe9ff8b31d72e76
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780251"
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Nasıl yapılır: Varlık ekleme, değiştirme ve silme (WCF Veri Hizmetleri)
İstemci kitaplıkları ile, <xref:System.Data.Services.Client.DataServiceContext>içindeki nesneler üzerinde eşdeğer eylemler gerçekleştirerek bir veri hizmetindeki varlık verilerini oluşturabilir, güncelleştirebilir ve silebilirsiniz. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext> yeni bir nesne örneği oluşturur ve sonra öğesini bağlamda <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> oluşturmak için üzerinde yöntemini çağırır. <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> Yöntemi çağrıldığında veri hizmetine bir http post iletisi gönderilir.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, var olan bir nesneyi alır ve değiştirir ve sonra öğesini <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> bağlamındaki öğesini güncelleştirilmiş <xref:System.Data.Services.Client.DataServiceContext> olarak işaretlemek için üzerinde yöntemini çağırır. <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> Yöntemi çağrıldığında veri hizmetine bir http birleştirme iletisi gönderilir.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> <xref:System.Data.Services.Client.DataServiceContext> öğesini bağlamdaki öğeyi silinmiş olarak işaretlemek için üzerinde yöntemini çağırır. Bir http Delete iletisi, <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntem çağrıldığında veri hizmetine gönderilir.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext> yeni bir nesne örneği oluşturur ve sonra öğesini bağlamda <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> , ilişkili siparişin bağlantısıyla birlikte oluşturmak için üzerinde yöntemini çağırır. <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> Yöntemi çağrıldığında veri hizmetine bir http post iletisi gönderilir.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Nasıl yapılır: DataServiceContext 'e mevcut bir varlık iliştirme](attach-an-existing-entity-to-dc-wcf-data.md)
- [Nasıl yapılır: Varlık Ilişkilerini tanımlama](how-to-define-entity-relationships-wcf-data-services.md)
- [Toplu İşlemler](batching-operations-wcf-data-services.md)
