---
title: Uç Noktası Performans Sayaçları
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 8354cff600f8c16a5ab9b4f6efd3c0b93a46276c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="7c256-102">Uç Noktası Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="7c256-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="7c256-103">Uç noktası performans sayaçlarını nasıl bir uç nokta iletileri kabul etmeye ortaya çıkarır verilerini yakalama.</span><span class="sxs-lookup"><span data-stu-id="7c256-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="7c256-104">Altında bulunabilir `ServiceModelEndpoint 4.0.0.0` Performans İzleyicisi ile görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7c256-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="7c256-105">Bu desen kullanılarak adlandırılmış örnekleri:</span><span class="sxs-lookup"><span data-stu-id="7c256-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="7c256-106">Verileri tek tek işlemleri için toplanan benzer, ancak yalnızca uç nokta toplanır.</span><span class="sxs-lookup"><span data-stu-id="7c256-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="7c256-107">Bir performans sayacı örneğinin adının uzunluğu bir sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="7c256-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="7c256-108">Bir Windows Communication Foundation (WCF) sayaç örneği adı uzunluk üst sınırını aşarsa, WCF örnek adının bir kısmını karma değeri ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="7c256-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c256-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c256-109">See Also</span></span>  
 [<span data-ttu-id="7c256-110">Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="7c256-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
