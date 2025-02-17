---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Sayfalanmış sonuçları yükleme (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: Sayfalanmış sonuçları yükleme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
ms.openlocfilehash: 2a5ba738a63de11045dec78f4381b93c844a4fc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765275"
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Nasıl yapılır: Sayfalanmış sonuçları yükleme (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Veri Hizmetleri, veri hizmetinin tek bir yanıt akışında döndürülen varlık sayısını sınırlayabilmesini sağlar. Bu durumda, akıştaki son giriş sonraki veri sayfasına bir bağlantı içerir. Sonraki veri sayfasının URI 'SI, <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> yürütüldüğünde döndürülen öğesinin metodu çağırarak elde edilir <xref:System.Data.Services.Client.QueryOperationResponse%601> <xref:System.Data.Services.Client.DataServiceQuery%601> . Bu nesne tarafından temsil edilen URI daha sonra sonuçların sonraki sayfasını yüklemek için kullanılır. Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](loading-deferred-content-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  

 Bu örnek `do…while` `Customers` , veri hizmetindeki disk belleğine alınmış sonuçlardan varlık yüklemek için bir döngü kullanır.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Örnek  

 Bu örnek `Orders` , her varlıkla ilgili varlıkları döndürür `Customers` ve `do…while` varlık sayfalarını yüklemek için bir döngü kullanır `Customers` ve `while` ilgili varlıkların sayfalarını veri hizmetinden yüklemek için iç içe geçmiş bir döngü kullanır `Orders` .  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ertelenmiş İçerik Yükleme](loading-deferred-content-wcf-data-services.md)
- [Nasıl yapılır: İlgili Varlıkları Yükleme](how-to-load-related-entities-wcf-data-services.md)
