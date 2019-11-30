---
title: "Nasıl yapılır: DataServiceContext 'e mevcut bir varlık Iliştirme (WCF Veri Hizmetleri)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
ms.openlocfilehash: 7c8355ea9e9823e7cab6f43c0f3f901948d1d539
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569373"
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>Nasıl yapılır: DataServiceContext 'e mevcut bir varlık Iliştirme (WCF Veri Hizmetleri)
Bir varlık bir veri hizmetinde zaten mevcutsa, WCF Veri Hizmetleri istemci kitaplığı, önce bir sorgu yürütmeden doğrudan <xref:System.Data.Services.Client.DataServiceContext> varlığı temsil eden bir nesne eklemenize olanak sağlar. Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, veri hizmetine kaydedilecek değişiklikleri içeren mevcut bir `Customer` nesnesinin nasıl oluşturulacağını gösterir. Nesne, içeriğe iliştirilir ve <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> yöntemi, <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılmadan önce, eklenen nesneyi <xref:System.Data.Services.Client.EntityStates.Modified> olarak işaretlemek için çağırılır.  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
