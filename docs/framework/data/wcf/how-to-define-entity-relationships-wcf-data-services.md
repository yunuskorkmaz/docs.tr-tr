---
title: 'Nasıl yapılır: varlık Ilişkilerini tanımlama (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: f693579883ae03a6c8df3e9a9f4941e1f9940a4c
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569114"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Nasıl yapılır: varlık Ilişkilerini tanımlama (WCF Veri Hizmetleri)
WCF Veri Hizmetleri yeni bir varlık eklediğinizde, yeni varlık ve ilgili varlıklar arasındaki ilişkiler otomatik olarak tanımlanmamıştır. Varlık örnekleri arasında ilişkiler oluşturabilir ve değiştirebilir ve istemci kitaplığının veri hizmetindeki değişiklikleri yansıtmasını sağlayabilirsiniz. Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yeni bir nesne örneği oluşturur ve sonra, öğeyi bağlamda oluşturmak için <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> yöntemini çağırarak ilgili siparişin bağlantısı ile birlikte. <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrıldığında veri hizmetine bir HTTP POST iletisi gönderilir.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bir `Products` nesnesine başvuru içeren ilgili bir `Orders` nesnesine `Order_Details` nesnesini eklemek için <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> yönteminin nasıl kullanılacağını gösterir. <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> ve <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> yöntemleri ilişkiyi tanımlar. Bu örnekte, `Order_Details` nesnesindeki gezinti özellikleri de açıkça ayarlanmıştır.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Nasıl yapılır: Varlık Ekleme, Değiştirme ve Silme](how-to-add-modify-and-delete-entities-wcf-data-services.md)
