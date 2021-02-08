---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir sorgu tarafından döndürülen varlıkların sayısını belirleme (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: bir sorgu tarafından döndürülen varlıkların sayısını belirleme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, row count
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
ms.openlocfilehash: f8eb305bc515d1d69025ce3bcd0a6a9f3baf8232
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794994"
---
# <a name="how-to-determine-the-number-of-entities-returned-by-a-query-wcf-data-services"></a>Nasıl yapılır: bir sorgu tarafından döndürülen varlıkların sayısını belirleme (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Veri Hizmetleri, bir sorgu URI 'SI tarafından belirtilen varlık kümesindeki varlıkların sayısını belirleyebilirsiniz. Bu sayı, sorgu sonucuyla birlikte veya bir tamsayı değeri olarak dahil edilebilir. Daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  

 Bu örnek, yöntemini çağırdıktan sonra bir sorgu yürütür <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> . <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A>Özelliği, varlık kümesindeki varlıkların sayısını döndürür `Customers` .  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomers)]  
  
## <a name="example"></a>Örnek  

 Bu örnek, <xref:System.Linq.Enumerable.Count%2A> yalnızca varlık kümesindeki varlıkların sayısı olan bir tamsayı değeri döndürecek şekilde yöntemini çağırır `Customers` .  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomersvalueonly)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
