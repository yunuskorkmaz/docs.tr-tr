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
ms.openlocfilehash: 1ef7fa93b5afdf664f22bd69d3fe3a3b17e98f18
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180718"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Nasıl yapılır: Ilgili varlıkları yükleme (WCF Veri Hizmetleri)

WCF Veri Hizmetleri içinde ilişkili varlıkları yüklemeniz gerektiğinde, <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> sınıfındaki yöntemini kullanabilirsiniz <xref:System.Data.Services.Client.DataServiceContext> . Ayrıca <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> , <xref:System.Data.Services.Client.DataServiceQuery%601> ilgili varlıkların aynı sorgu yanıtına de yüklenmesini gerektirmek için üzerinde yöntemini de kullanabilirsiniz.  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Customer` döndürülen her örnekle ilişkili olan öğesini açıkça yüklemeyi gösterir `Orders` .  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> `Order Details` sorgu tarafından döndürülen öğesine ait döndürmek için yönteminin nasıl kullanılacağını gösterir `Orders` .  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
