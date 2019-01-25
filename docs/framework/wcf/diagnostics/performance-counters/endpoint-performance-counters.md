---
title: Uç Noktası Performans Sayaçları
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: de750b3e5ee61b6bfc5b387fb7de84b74171d8d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501967"
---
# <a name="endpoint-performance-counters"></a>Uç Noktası Performans Sayaçları
Uç nokta performans sayaçları, bir uç nokta ileti nasıl kabul ortaya çıkarır verilerini yakalama. Altında bulunabilir `ServiceModelEndpoint 4.0.0.0` ile performans izleme görüntülerken Performans nesnesi. Örnekler, bu deseni kullanılarak adlandırılır:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Verileri tek işlemler için toplanan benzer, ancak yalnızca uç nokta toplanır.  
  
> [!CAUTION]
>  Bir performans sayacı örneğinin adının uzunluğu üzerinde bir sınır yoktur. Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aşıyor, WCF örnek adının bir kısmını bir karma değer ile değiştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Performans Sayaçları](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
