---
title: 'Nasıl yapılır: veri hizmeti sonuçlarının sayfalama özelliğini etkinleştirme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 6b7cea2475a5c11091a04ef3044bbc958e55fc5d
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569088"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Nasıl yapılır: veri hizmeti sonuçlarının sayfalama özelliğini etkinleştirme (WCF Veri Hizmetleri)
WCF Veri Hizmetleri, bir veri hizmeti sorgusunun döndürdüğü varlıkların sayısını sınırlamanıza olanak sağlar. Sayfa sınırları, hizmet başlatıldığında çağrılan yönteminde tanımlanır ve her bir varlık kümesi için ayrı ayrı ayarlanabilir.  
  
 Sayfalama etkinleştirildiğinde akıştaki son giriş, bir sonraki veri sayfasına bir bağlantı içerir. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md).  
  
 Bu konuda, döndürülen `Customers` ve `Orders` varlık kümelerinin sayfalama özelliğini etkinleştirmek için bir veri hizmetinin nasıl değiştirileceği gösterilmektedir. Bu konudaki örnek, Northwind örnek veri hizmetini kullanır. Bu hizmet, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Döndürülen müşterilerin ve sipariş varlık kümelerinin sayfalama özelliğini etkinleştirme  
  
- Veri Hizmeti kodunda, `InitializeService` işlevindeki yer tutucu kodunu aşağıdaki gibi değiştirin:  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ertelenmiş İçerik Yükleme](loading-deferred-content-wcf-data-services.md)
- [Nasıl yapılır: Sayfalanmış Sonuçları Yükleme](how-to-load-paged-results-wcf-data-services.md)
