---
title: 'Nasıl yapılır: Varlık ilişkileri (WCF Veri Hizmetleri) tanımlayın'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: 3bd2293f02e77ab2db5c3ba245596021e08b04c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875907"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Nasıl yapılır: Varlık ilişkileri (WCF Veri Hizmetleri) tanımlayın
Yeni bir varlıkta eklediğinizde [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], yeni varlık ve ilgili varlıkları arasındaki ilişkileri otomatik olarak tanımlanmamış. Oluşturma ve ilişkileri varlık örnekleri arasında değiştirme ve veri hizmeti bu değişiklikleri yansıtmak için istemci kitaplığını sahiptir. Daha fazla bilgi için [veri hizmetini güncelleştirme](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulan istemci veri hizmeti sınıfları kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir nesne örneği oluşturur ve <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> metodunda <xref:System.Data.Services.Client.DataServiceContext> ilgili sipariş bağlantısını birlikte bağlamında öğesi oluşturmak için. Veriler için bir HTTP POST iletisi gönderilir ne zaman hizmet <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılır.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> yöntemi eklemek için bir `Order_Details` ilgili nesnesine `Orders` nesne belirli bir başvuru ile `Products` nesne. <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> Ve <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> yöntemleri, ilişkileri tanımlayın. Bu örnekte, gezinti özellikleri `Order_Details` nesne de açıkça ayarlayın.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Nasıl yapılır: Ekleme, değiştirme ve varlıklarını silme](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md)
