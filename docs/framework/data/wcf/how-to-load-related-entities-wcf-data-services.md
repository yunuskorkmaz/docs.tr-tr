---
title: 'Nasıl yapılır: İlgili varlıkları (WCF Veri Hizmetleri) yükleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 75e1d583d2a4d519619a440800cdeb1403fedac2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936502"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Nasıl yapılır: İlgili varlıkları (WCF Veri Hizmetleri) yükleme
İlişkili varlıklar yüklemek gerektiğinde [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], kullanabileceğiniz <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metodunda <xref:System.Data.Services.Client.DataServiceContext> sınıfı. Ayrıca <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metodunda <xref:System.Data.Services.Client.DataServiceQuery%601> ilgili varlıkları aynı sorgu yanıtına eagerly yüklenmesini zorunlu tutmak için.  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulan istemci veri hizmeti sınıfları kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, açıkça yüklemek gösterilmektedir `Customer` , ilgili her döndürülen `Orders` örneği.  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> döndürülecek yöntemi `Order Details` için ait olan `Orders` sorgu tarafından döndürülen.  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
