---
description: "Şu konuda daha fazla bilgi edinin: nasıl yapılır: mevcut bir varlığı DataServiceContext 'e Iliştirme (WCF Veri Hizmetleri)"
title: "Nasıl yapılır: DataServiceContext 'e mevcut bir varlık Iliştirme (WCF Veri Hizmetleri)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
ms.openlocfilehash: 039225ec992a4ddd23fd9f7013e04562f6fe72a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766601"
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>Nasıl yapılır: DataServiceContext 'e mevcut bir varlık Iliştirme (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

Bir varlık bir veri hizmetinde zaten mevcutsa, WCF Veri Hizmetleri istemci kitaplığı, <xref:System.Data.Services.Client.DataServiceContext> ilk olarak bir sorgu yürütmeden varlığı temsil eden bir nesneyi doğrudan öğesine eklemenize olanak sağlar. Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Customer` veri hizmetine kaydedilecek değişiklikleri içeren var olan bir nesnenin nasıl oluşturulacağını gösterir. Nesnesi bağlamına iliştirilir ve yöntemi <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> <xref:System.Data.Services.Client.EntityStates.Modified> , yöntemi çağrılmadan önce, eklenen nesneyi işaretlemek için çağırılır <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> .  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
