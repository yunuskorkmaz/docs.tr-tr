---
title: "Uç Noktası Performans Sayaçları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d34df7c70e0edeef831843d9afcb2db32422ebe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-performance-counters"></a>Uç Noktası Performans Sayaçları
Uç noktası performans sayaçlarını nasıl bir uç nokta iletileri kabul etmeye ortaya çıkarır verilerini yakalama. Altında bulunabilir `ServiceModelEndpoint 4.0.0.0` Performans İzleyicisi ile görüntülerken Performans nesnesi. Bu desen kullanılarak adlandırılmış örnekleri:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Verileri tek tek işlemleri için toplanan benzer, ancak yalnızca uç nokta toplanır.  
  
> [!CAUTION]
>  Bir performans sayacı örneğinin adının uzunluğu bir sınırı yoktur. Zaman bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] sayaç örneği adı en fazla uzunluğu aşıyor [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] örnek adının bir kısmını karma değeri ile değiştirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans sayaçları](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
