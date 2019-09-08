---
title: 'Nasıl yapılır: Zaman uyumsuz veri hizmeti sorguları yürütme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
ms.openlocfilehash: 14bfc138c5ece45184fb939f19aaf3d7e73e7294
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790577"
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>Nasıl yapılır: Zaman uyumsuz veri hizmeti sorguları yürütme (WCF Veri Hizmetleri)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığını kullanarak, sorguları yürütme ve değişiklikleri kaydetme gibi istemci-sunucu işlemlerini zaman uyumsuz olarak gerçekleştirebilirsiniz. Daha fazla bilgi için bkz. [zaman uyumsuz işlemler](asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
> Geri aramanın belirli bir iş parçacığında çağrılması gereken bir uygulamada, <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> yönteminin yürütülmesini açıkça sıramalısınız. Daha fazla bilgi için bkz. [zaman uyumsuz işlemler](asynchronous-operations-wcf-data-services.md).  
  
 Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sorguyu başlatmak için <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> yöntemini çağırarak zaman uyumsuz bir sorgunun nasıl yürütüleceğini gösterir. Satır içi temsilci, sorgu <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> sonuçlarını göstermek için yöntemini çağırır.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
