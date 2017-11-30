---
title: "Nasıl yapılır: veri hizmeti sonuçları (WCF Veri Hizmetleri) ICollection"
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
helpviewer_keywords: paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6bf267cdc4ab3ec3bdc82a3da52cef21ef1d6b2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Nasıl yapılır: veri hizmeti sonuçları (WCF Veri Hizmetleri) ICollection
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]bir veri hizmeti sorgu tarafından döndürülen varlık sayısını sınırlamanıza olanak sağlar. Sayfa sınırlarını hizmeti başlatılır ve her varlık kümesi için ayrı ayrı ayarlanabilir çağrılan yöntem tanımlanır.  
  
 Sayfalama etkin olduğunda, son girişi akıştaki verilerin bir sonraki sayfaya bir bağlantı içerir. Daha fazla bilgi için bkz: [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Bu konu, disk belleği etkinleştirmek için veri hizmeti değiştirmek nasıl gösterir döndürülen `Customers` ve `Orders` varlık kümeleri. Bu konudaki örnek Northwind örnek veri hizmeti kullanır. Bu hizmeti tamamladığınızda oluşturulan [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Disk belleği döndürülen müşteriler ve siparişler varlık kümelerinin etkinleştirme  
  
-   Veri Hizmeti için kodda yer tutucu kodu `InitializeService` aşağıdaki işleviyle:  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İçerik yükleme ertelenmiş](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [Nasıl yapılır: yük sonuçları disk belleği](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
