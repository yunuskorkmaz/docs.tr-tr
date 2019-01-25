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
# <a name="endpoint-performance-counters"></a><span data-ttu-id="477cd-102">Uç Noktası Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="477cd-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="477cd-103">Uç nokta performans sayaçları, bir uç nokta ileti nasıl kabul ortaya çıkarır verilerini yakalama.</span><span class="sxs-lookup"><span data-stu-id="477cd-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="477cd-104">Altında bulunabilir `ServiceModelEndpoint 4.0.0.0` ile performans izleme görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="477cd-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="477cd-105">Örnekler, bu deseni kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="477cd-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="477cd-106">Verileri tek işlemler için toplanan benzer, ancak yalnızca uç nokta toplanır.</span><span class="sxs-lookup"><span data-stu-id="477cd-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="477cd-107">Bir performans sayacı örneğinin adının uzunluğu üzerinde bir sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="477cd-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="477cd-108">Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aşıyor, WCF örnek adının bir kısmını bir karma değer ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="477cd-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="477cd-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="477cd-109">See also</span></span>
- [<span data-ttu-id="477cd-110">Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="477cd-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
