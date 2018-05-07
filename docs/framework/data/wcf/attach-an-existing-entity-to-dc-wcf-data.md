---
title: 'Nasıl yapılır: DataServiceContext (WCF Veri Hizmetleri) var olan bir varlık ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
ms.openlocfilehash: 30a0c0eb618dc7cedc8be2be4a327d9b1f73a51b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>Nasıl yapılır: DataServiceContext (WCF Veri Hizmetleri) var olan bir varlık ekleme
Bir varlığın bir veri hizmeti zaten mevcut olduğunda [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı, varlık doğrudan temsil eden bir nesne eklemek tanır <xref:System.Data.Services.Client.DataServiceContext> ilk bir sorgu yürütme. Daha fazla bilgi için bkz: [veri hizmeti güncelleştirme](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulur istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek varolan oluşturulacağını gösterir `Customer` veri hizmetine kaydedilmesi için değişiklikler içeren nesne. Nesne bağlamına bağlı olduğu ve <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> yöntemi ekli nesnesi olarak işaretlemek için çağrılır <xref:System.Data.Services.Client.EntityStates.Modified> önce <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılır.  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
