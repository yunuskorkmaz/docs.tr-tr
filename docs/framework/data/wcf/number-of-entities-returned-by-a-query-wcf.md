---
title: 'Nasıl yapılır: (WCF Veri Hizmetleri) bir sorgu tarafından döndürülen varlık sayısını belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, row count
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
ms.openlocfilehash: cc4ada3dabe20927f4c3a27dbb0fda78e41452c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683079"
---
# <a name="how-to-determine-the-number-of-entities-returned-by-a-query-wcf-data-services"></a>Nasıl yapılır: (WCF Veri Hizmetleri) bir sorgu tarafından döndürülen varlık sayısını belirleme
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], varlık kümesi bir URI sorgu tarafından belirtilen bulunan varlık sayısını belirleyebilirsiniz. Bu sayı, sorgu sonucu birlikte ya da bir tamsayı değeri olarak dahil edilebilir. Daha fazla bilgi için [veri hizmetini sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulan istemci veri hizmeti sınıfları kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek bir sorgu çağırdıktan sonra yürütür <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> yöntemi. <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> Özelliği varlıkların sayısı döndürür `Customers` varlık kümesi.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#countallcustomers)]  
  
## <a name="example"></a>Örnek  
 Bu örnek <xref:System.Linq.Enumerable.Count%2A> yöntemi yalnızca bir tamsayı döndürülecek değeri varlıkların sayısı `Customers` varlık kümesi.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#countallcustomersvalueonly)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
