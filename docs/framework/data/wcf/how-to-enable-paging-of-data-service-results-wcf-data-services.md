---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: veri hizmeti sonuçlarının sayfalamayı etkinleştirme (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: veri hizmeti sonuçlarının sayfalama özelliğini etkinleştirme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 27a2b37f432d906022d06492b2f687681d9b9ac8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765340"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Nasıl yapılır: veri hizmeti sonuçlarının sayfalama özelliğini etkinleştirme (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Veri Hizmetleri, bir veri hizmeti sorgusunun döndürdüğü varlıkların sayısını sınırlamanıza olanak sağlar. Sayfa sınırları, hizmet başlatıldığında çağrılan yönteminde tanımlanır ve her bir varlık kümesi için ayrı ayrı ayarlanabilir.  
  
 Sayfalama etkinleştirildiğinde akıştaki son giriş, bir sonraki veri sayfasına bir bağlantı içerir. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md).  
  
 Bu konuda `Customers` , döndürülen ve varlık kümelerinin sayfalama özelliğini etkinleştirmek için bir veri hizmetinin nasıl değiştirileceği gösterilmektedir `Orders` . Bu konudaki örnek, Northwind örnek veri hizmetini kullanır. Bu hizmet, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Döndürülen müşterilerin ve sipariş varlık kümelerinin sayfalama özelliğini etkinleştirme  
  
- Veri Hizmeti kodunda, işlevdeki yer tutucu kodunu aşağıdaki gibi değiştirin `InitializeService` :  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ertelenmiş İçerik Yükleme](loading-deferred-content-wcf-data-services.md)
- [Nasıl yapılır: Sayfalanmış Sonuçları Yükleme](how-to-load-paged-results-wcf-data-services.md)
