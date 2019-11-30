---
title: 'Nasıl yapılır: Sayfalanmış sonuçları yükleme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
ms.openlocfilehash: d651a66ac619e46d3ec6b46b194436f51300ff25
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569032"
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Nasıl yapılır: Sayfalanmış sonuçları yükleme (WCF Veri Hizmetleri)
WCF Veri Hizmetleri, veri hizmetinin tek bir yanıt akışında döndürülen varlık sayısını sınırlayabilmesini sağlar. Bu durumda, akıştaki son giriş sonraki veri sayfasına bir bağlantı içerir. Sonraki veri sayfasının URI 'SI, <xref:System.Data.Services.Client.DataServiceQuery%601> yürütüldüğünde döndürülen <xref:System.Data.Services.Client.QueryOperationResponse%601><xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> yöntemi çağırarak elde edilir. Bu nesne tarafından temsil edilen URI daha sonra sonuçların sonraki sayfasını yüklemek için kullanılır. Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](loading-deferred-content-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Bu örnek, veri hizmetindeki disk belleğine alınmış sonuçlardan `Customers` varlıkları yüklemek için `do…while` döngüsünü kullanır.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, her bir `Customers` varlıkla ilgili `Orders` varlıkları döndürür ve ilgili `while` varlıklarının sayfalarını veri hizmetinden yüklemek için `do…while` `Customers` döngüsünü kullanır.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ertelenmiş İçerik Yükleme](loading-deferred-content-wcf-data-services.md)
- [Nasıl yapılır: İlgili Varlıkları Yükleme](how-to-load-related-entities-wcf-data-services.md)
