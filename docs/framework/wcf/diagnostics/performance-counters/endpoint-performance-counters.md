---
title: Uç Noktası Performans Sayaçları
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 2352bc82998c8e87e72f331104446bac4fcb9fda
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040580"
---
# <a name="endpoint-performance-counters"></a>Uç Noktası Performans Sayaçları
Uç nokta performans sayaçları, bir uç noktanın iletileri nasıl kabul ettiğini gösteren verileri yakalar. Performans İzleyicisi ile görüntülenirken `ServiceModelEndpoint 4.0.0.0` performans nesnesi altında bulunabilir. Örnekler bu model kullanılarak adlandırılır:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Veriler tek tek işlemler için toplanmaya benzerdir, ancak yalnızca uç nokta boyunca toplanır.  
  
> [!CAUTION]
> Performans sayacı örneğinin adının uzunluğu için bir sınır vardır. Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aştığında, WCF örnek adının bir bölümünü bir karma değerle değiştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans Sayaçları](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
