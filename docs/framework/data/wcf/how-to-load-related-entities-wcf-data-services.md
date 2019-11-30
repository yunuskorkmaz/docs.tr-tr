---
title: 'Nasıl yapılır: Ilgili varlıkları yükleme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 84c2448f317e813a95688feaaac1c97436de1b16
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569012"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Nasıl yapılır: Ilgili varlıkları yükleme (WCF Veri Hizmetleri)
WCF Veri Hizmetleri içinde ilişkili varlıkları yüklemeniz gerektiğinde <xref:System.Data.Services.Client.DataServiceContext> sınıfında <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> yöntemini kullanabilirsiniz. Aynı sorgu yanıtında ilgili varlıkların de aynı şekilde yüklenmesini gerektirmek için <xref:System.Data.Services.Client.DataServiceQuery%601> <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yöntemini de kullanabilirsiniz.  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, döndürülen her `Orders` örnekle ilgili `Customer` açıkça yüklemeyi gösterir.  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sorgu tarafından döndürülen `Orders` ait `Order Details` döndürmek için <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yönteminin nasıl kullanılacağını gösterir.  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
