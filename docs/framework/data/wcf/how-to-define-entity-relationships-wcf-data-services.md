---
title: 'Nasıl yapılır: Varlık Ilişkilerini tanımlama (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: 63714f97e691b2ba0177a36a599b62ca7681dcf6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790641"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Nasıl yapılır: Varlık Ilişkilerini tanımlama (WCF Veri Hizmetleri)
İçinde [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]yeni bir varlık eklediğinizde, yeni varlık ve ilgili varlıklar arasındaki ilişkiler otomatik olarak tanımlanmamıştır. Varlık örnekleri arasında ilişkiler oluşturabilir ve değiştirebilir ve istemci kitaplığının veri hizmetindeki değişiklikleri yansıtmasını sağlayabilirsiniz. Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext> yeni bir nesne örneği oluşturur ve sonra öğesini bağlamda <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> , ilişkili siparişin bağlantısıyla birlikte oluşturmak için üzerinde yöntemini çağırır. <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> Yöntemi çağrıldığında veri hizmetine bir http post iletisi gönderilir.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> , belirli `Orders` `Order_Details` bir`Products` nesneye başvuru içeren ilgili nesneye bir nesne eklemek için yönteminin nasıl kullanılacağını gösterir. <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> Ve<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> yöntemleri ilişkiyi tanımlar. Bu örnekte, `Order_Details` nesne üzerindeki gezinti özellikleri de açıkça ayarlanır.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Nasıl yapılır: Varlık ekleme, değiştirme ve silme](how-to-add-modify-and-delete-entities-wcf-data-services.md)
