---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: varlık Ilişkilerini tanımlama (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: varlık Ilişkilerini tanımlama (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: 08add639fe333d4892737c64b12ca370129d0bf7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765522"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Nasıl yapılır: varlık Ilişkilerini tanımlama (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Veri Hizmetleri yeni bir varlık eklediğinizde, yeni varlık ve ilgili varlıklar arasındaki ilişkiler otomatik olarak tanımlanmamıştır. Varlık örnekleri arasında ilişkiler oluşturabilir ve değiştirebilir ve istemci kitaplığının veri hizmetindeki değişiklikleri yansıtmasını sağlayabilirsiniz. Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, yeni bir nesne örneği oluşturur ve sonra <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> <xref:System.Data.Services.Client.DataServiceContext> öğesini bağlamda, ilişkili siparişin bağlantısıyla birlikte oluşturmak için üzerinde yöntemini çağırır. Yöntemi çağrıldığında veri hizmetine bir HTTP POST iletisi gönderilir <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> .  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> `Order_Details` belirli bir `Orders` nesneye başvuru içeren ilgili nesneye bir nesne eklemek için yönteminin nasıl kullanılacağını gösterir `Products` . <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>Ve <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> yöntemleri ilişkiyi tanımlar. Bu örnekte, nesne üzerindeki gezinti özellikleri `Order_Details` de açıkça ayarlanır.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Nasıl yapılır: Varlık Ekleme, Değiştirme ve Silme](how-to-add-modify-and-delete-entities-wcf-data-services.md)
