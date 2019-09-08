---
title: 'Nasıl yapılır: Ilgili varlıkları yükle (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 14b0ba988c96c270610208a4f944083bb333eac5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780019"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Nasıl yapılır: Ilgili varlıkları yükle (WCF Veri Hizmetleri)
İçinde [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]ilişkili varlıkları yüklemeniz gerektiğinde, <xref:System.Data.Services.Client.DataServiceContext> sınıfındaki <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> yöntemini kullanabilirsiniz. Ayrıca, <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> <xref:System.Data.Services.Client.DataServiceQuery%601> ilgili varlıkların aynı sorgu yanıtına de yüklenmesini gerektirmek için üzerinde yöntemini de kullanabilirsiniz.  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, döndürülen `Customer` `Orders` her örnekle ilişkili olan öğesini açıkça yüklemeyi gösterir.  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sorgu tarafından <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> `Orders` döndürülen öğesine ait döndürmek `Order Details` için yönteminin nasıl kullanılacağını gösterir.  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
