---
title: "Nasıl yapılır: yük havuzda sonuçları (WCF Veri Hizmetleri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 91414ac4d392b9c042c9e236d2bfb69b44ead4ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Nasıl yapılır: yük havuzda sonuçları (WCF Veri Hizmetleri)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Akış tek bir yanıtta döndürülen varlıkları sayısını sınırlamak veri hizmeti sağlar. Bu durumda, son girişi akıştaki verilerin bir sonraki sayfaya bir bağlantı içerir. Sonraki sayfanın veri URI'sini çağırılarak alınır <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> yöntemi <xref:System.Data.Services.Client.QueryOperationResponse%601>, hangi döndürülür ne zaman <xref:System.Data.Services.Client.DataServiceQuery%601> yürütülür. Bu nesne tarafından temsil edilen URI, ardından sonraki sonuç sayfasını yüklemek için kullanılır. Daha fazla bilgi için bkz: [ertelenmiş içerik yüklenirken](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulur istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte bir `do…while` yüklemek için döngü `Customers` disk belleğine alınmış sonuçlar veri hizmetinden varlıklardan.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Örnek  
 Bu örnek ilgili döndürür `Orders` her varlıklarıyla `Customers` varlık ve kullanır bir `do…while` yüklemek için döngü `Customers` varlıklar sayfaları ve iç içe bir `while` ilgili sayfaları yüklemek için döngü `Orders` veri hizmeti varlıkları .  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İçerik yükleme ertelenmiş](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [Nasıl yapılır: ilgili varlıklar yükleme](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md)
