---
title: 'Nasıl yapılır: (WCF Veri Hizmetleri) veri hizmeti sonuçlarını sayfalamayı etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: edc150d118153849dd84eb40f1443d842c7d346d
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517848"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Nasıl yapılır: (WCF Veri Hizmetleri) veri hizmeti sonuçlarını sayfalamayı etkinleştirme
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir veri hizmeti sorgu tarafından döndürülen varlık sayısını sınırlamak sağlar. Sayfa sınırlarını hizmeti başlatılır ve ayrı olarak her varlık kümesi için ayarlanabilir çağrılan yöntem tanımlanır.  
  
 Sayfalama etkin olduğunda, son girişi akıştaki verilerin bir sonraki sayfaya bir bağlantı içerir. Daha fazla bilgi için [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Bu konuda, disk belleğini etkinleştirmek için bir veri hizmeti değiştirme işlemi gösterilmektedir döndürülen `Customers` ve `Orders` varlık kümesi. Bu konudaki örnek Northwind örnek veri hizmeti kullanır. Bu hizmet, tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Döndürülen müşteriler ve siparişler varlık kümeleri sayfalamayı etkinleştirme  
  
-   Veri Hizmeti için kodda yer tutucusunu değiştirin `InitializeService` işlevi aşağıdaki:  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ertelenmiş İçerik Yükleme](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)
- [Nasıl yapılır: Disk belleği sonuçları](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
