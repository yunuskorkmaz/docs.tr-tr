---
title: 'Nasıl yapılır: bir sorgu tarafından döndürülen varlıkların sayısını belirleme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, row count
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
ms.openlocfilehash: 43833566d59b15ef382872b0c40f452192b59bac
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568922"
---
# <a name="how-to-determine-the-number-of-entities-returned-by-a-query-wcf-data-services"></a>Nasıl yapılır: bir sorgu tarafından döndürülen varlıkların sayısını belirleme (WCF Veri Hizmetleri)
WCF Veri Hizmetleri, bir sorgu URI 'SI tarafından belirtilen varlık kümesindeki varlıkların sayısını belirleyebilirsiniz. Bu sayı, sorgu sonucuyla birlikte veya bir tamsayı değeri olarak dahil edilebilir. Daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> yöntemini çağırdıktan sonra bir sorgu yürütür. <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> özelliği, `Customers` varlık kümesindeki varlıkların sayısını döndürür.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomers)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, yalnızca `Customers` varlık kümesindeki varlıkların sayısı olan bir tamsayı değeri döndürmek için <xref:System.Linq.Enumerable.Count%2A> yöntemini çağırır.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomersvalueonly)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
