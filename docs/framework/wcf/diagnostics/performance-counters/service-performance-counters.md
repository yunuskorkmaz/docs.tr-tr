---
description: 'Daha fazla bilgi edinin: hizmet performansı sayaçları'
title: Hizmet Performansı Sayaçları
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 16f6f2548cf7f92b64264ac606423c69e62cd110
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686043"
---
# <a name="service-performance-counters"></a><span data-ttu-id="df3eb-103">Hizmet Performansı Sayaçları</span><span class="sxs-lookup"><span data-stu-id="df3eb-103">Service Performance Counters</span></span>

<span data-ttu-id="df3eb-104">Hizmet performans sayaçları, hizmet davranışını bir bütün olarak ölçer ve tüm hizmetin performansını tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="df3eb-104">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="df3eb-105">Performans `ServiceModelService 4.0.0.0` İzleyicisi (Perfmon.exe) ile görüntülenirken Performans nesnesi altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="df3eb-105">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="df3eb-106">Örnekler aşağıdaki model kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="df3eb-106">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> <span data-ttu-id="df3eb-107">Performans sayacı örneğinin adının uzunluğu için bir sınır vardır.</span><span class="sxs-lookup"><span data-stu-id="df3eb-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="df3eb-108">Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aştığında, WCF örnek adının bir bölümünü bir karma değerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="df3eb-108">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df3eb-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df3eb-109">See also</span></span>

- [<span data-ttu-id="df3eb-110">Performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="df3eb-110">Performance Counters</span></span>](index.md)
