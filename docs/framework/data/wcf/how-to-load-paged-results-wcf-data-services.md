---
title: 'Nasıl yapılır: Yük disk belleği sonuçları (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
ms.openlocfilehash: 0be7dcbefb23d2f2b283ac498f3b0ea43278f2d4
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517258"
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Nasıl yapılır: Yük disk belleği sonuçları (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Akış tek bir yanıtta döndürülen varlık sayısını sınırlamak veri hizmeti sağlar. Bu durumda, son giriş akıştaki verilerin bir sonraki sayfaya bir bağlantı içerir. Sonraki sayfanın veri URI'si çağırılarak alınır <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> yöntemi <xref:System.Data.Services.Client.QueryOperationResponse%601>, getirilen ne zaman <xref:System.Data.Services.Client.DataServiceQuery%601> yürütülür. Bu nesne tarafından temsil edilen URI'nin sonra sonraki sonuç sayfasını yüklemek için kullanılır. Daha fazla bilgi için [ertelenmiş içerik yükleme](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulan istemci veri hizmeti sınıfları kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte bir `do…while` yüklemek için döngü `Customers` varlıkları data Service'ten bir disk belleğine alınmış sonuçlar.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte ilgili döndürür `Orders` her varlıklarla `Customers` varlık ve kullandığı bir `do…while` yüklemek için döngü `Customers` varlıkları sayfaları ve iç içe bir `while` ilgili sayfaları yüklemek için döngü `Orders` varlıkları data Service'ten .  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ertelenmiş İçerik Yükleme](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)
- [Nasıl yapılır: İlgili varlıkları yükleme](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md)
