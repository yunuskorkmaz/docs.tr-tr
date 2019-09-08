---
title: "Nasıl yapılır: DataServiceContext 'e mevcut bir varlık iliştirme (WCF Veri Hizmetleri)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
ms.openlocfilehash: 160f0afc2e1baf033557b7114a51145a5c983e29
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791188"
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>Nasıl yapılır: DataServiceContext 'e mevcut bir varlık iliştirme (WCF Veri Hizmetleri)
Bir varlık bir veri hizmetinde zaten mevcutsa, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı, önce bir sorgu yürütmeden, <xref:System.Data.Services.Client.DataServiceContext> varlığı temsil eden bir nesneyi doğrudan öğesine eklemenize olanak sağlar. Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, veri hizmetine kaydedilecek değişiklikleri içeren var `Customer` olan bir nesnenin nasıl oluşturulacağını gösterir. Nesnesi bağlamına iliştirilir ve <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> yöntemi, <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılmadan <xref:System.Data.Services.Client.EntityStates.Modified> önce, eklenen nesneyi işaretlemek için çağırılır.  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
