---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Ilgili varlıkları yükleme (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: Ilgili varlıkları yükleme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 004e52b17c399abe8564dd069dd251d7baf296cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765262"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Nasıl yapılır: Ilgili varlıkları yükleme (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

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
