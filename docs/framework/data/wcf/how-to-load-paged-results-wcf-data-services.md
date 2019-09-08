---
title: 'Nasıl yapılır: Sayfalanmış sonuçları yükle (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
ms.openlocfilehash: e718aad904a43d118a243afafc17834cba31f028
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790450"
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Nasıl yapılır: Sayfalanmış sonuçları yükle (WCF Veri Hizmetleri)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]veri hizmetinin tek bir yanıt akışında döndürülen varlık sayısını sınırlayabilmesini sağlar. Bu durumda, akıştaki son giriş sonraki veri sayfasına bir bağlantı içerir. Sonraki veri sayfasının URI 'si, yürütüldüğünde döndürülen <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> <xref:System.Data.Services.Client.QueryOperationResponse%601> <xref:System.Data.Services.Client.DataServiceQuery%601> öğesinin metodu çağırarak elde edilir. Bu nesne tarafından temsil edilen URI daha sonra sonuçların sonraki sayfasını yüklemek için kullanılır. Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](loading-deferred-content-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Bu örnek, veri `do…while` hizmetindeki disk belleğine `Customers` alınmış sonuçlardan varlık yüklemek için bir döngü kullanır.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, her `Orders` `Customers` varlıkla ilgili varlıkları döndürür ve veri hizmetinden `do…while` ilgili `Orders` varlıkların sayfalarını `Customers` yüklemek için varlık sayfalarını ve `while` iç içe geçmiş bir döngüyü yüklemek için bir döngü kullanır .  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ertelenmiş İçerik Yükleme](loading-deferred-content-wcf-data-services.md)
- [Nasıl yapılır: Ilgili varlıkları yükle](how-to-load-related-entities-wcf-data-services.md)
