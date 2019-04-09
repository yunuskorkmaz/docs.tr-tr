---
title: Uç Noktası Performans Sayaçları
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: f07e318e39a68e689ec484b09fa743623cfb51d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158399"
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="98885-102">Uç Noktası Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="98885-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="98885-103">Uç nokta performans sayaçları, bir uç nokta ileti nasıl kabul ortaya çıkarır verilerini yakalama.</span><span class="sxs-lookup"><span data-stu-id="98885-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="98885-104">Altında bulunabilir `ServiceModelEndpoint 4.0.0.0` ile performans izleme görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="98885-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="98885-105">Örnekler, bu deseni kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="98885-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="98885-106">Verileri tek işlemler için toplanan benzer, ancak yalnızca uç nokta toplanır.</span><span class="sxs-lookup"><span data-stu-id="98885-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="98885-107">Bir performans sayacı örneğinin adının uzunluğu üzerinde bir sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="98885-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="98885-108">Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aşıyor, WCF örnek adının bir kısmını bir karma değer ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="98885-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98885-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98885-109">See also</span></span>

- [<span data-ttu-id="98885-110">Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="98885-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
