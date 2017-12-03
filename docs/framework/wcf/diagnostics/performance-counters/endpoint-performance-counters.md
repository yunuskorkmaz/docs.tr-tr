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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 157f0cc5d860841940b0850ca3895f82a12d47ce
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="baad5-102">Uç Noktası Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="baad5-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="baad5-103">Uç noktası performans sayaçlarını nasıl bir uç nokta iletileri kabul etmeye ortaya çıkarır verilerini yakalama.</span><span class="sxs-lookup"><span data-stu-id="baad5-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="baad5-104">Altında bulunabilir `ServiceModelEndpoint 4.0.0.0` Performans İzleyicisi ile görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="baad5-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="baad5-105">Bu desen kullanılarak adlandırılmış örnekleri:</span><span class="sxs-lookup"><span data-stu-id="baad5-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="baad5-106">Verileri tek tek işlemleri için toplanan benzer, ancak yalnızca uç nokta toplanır.</span><span class="sxs-lookup"><span data-stu-id="baad5-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="baad5-107">Bir performans sayacı örneğinin adının uzunluğu bir sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="baad5-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="baad5-108">Zaman bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] sayaç örneği adı en fazla uzunluğu aşıyor [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] örnek adının bir kısmını karma değeri ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="baad5-108">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baad5-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="baad5-109">See Also</span></span>  
 [<span data-ttu-id="baad5-110">Performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="baad5-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
