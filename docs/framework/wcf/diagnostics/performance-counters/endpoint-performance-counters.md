---
title: Uç Noktası Performans Sayaçları
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: cdddd8be962df0b295eb394fcaba3756e8a1a50f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237969"
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="22f81-102">Uç Noktası Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="22f81-102">Endpoint Performance Counters</span></span>

<span data-ttu-id="22f81-103">Uç nokta performans sayaçları, bir uç noktanın iletileri nasıl kabul ettiğini gösteren verileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="22f81-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="22f81-104">Performans `ServiceModelEndpoint 4.0.0.0` İzleyicisi ile görüntülenirken Performans nesnesi altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="22f81-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="22f81-105">Örnekler bu model kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="22f81-105">The instances are named using this pattern:</span></span>  
  
`(ServiceName).(ContractName)@(endpoint listener address)`  
  
 <span data-ttu-id="22f81-106">Veriler tek tek işlemler için toplanmaya benzerdir, ancak yalnızca uç nokta boyunca toplanır.</span><span class="sxs-lookup"><span data-stu-id="22f81-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="22f81-107">Performans sayacı örneğinin adının uzunluğu için bir sınır vardır.</span><span class="sxs-lookup"><span data-stu-id="22f81-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="22f81-108">Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aştığında, WCF örnek adının bir bölümünü bir karma değerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="22f81-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f81-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22f81-109">See also</span></span>

- [<span data-ttu-id="22f81-110">Performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="22f81-110">Performance Counters</span></span>](index.md)
