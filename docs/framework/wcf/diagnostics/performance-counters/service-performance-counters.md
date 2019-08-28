---
title: Hizmet Performansı Sayaçları
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 18a9e6336b70341f5da9c7b73cbd3f9bd3f958c7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044268"
---
# <a name="service-performance-counters"></a><span data-ttu-id="9033a-102">Hizmet Performansı Sayaçları</span><span class="sxs-lookup"><span data-stu-id="9033a-102">Service Performance Counters</span></span>
<span data-ttu-id="9033a-103">Hizmet performans sayaçları, hizmet davranışını bir bütün olarak ölçer ve tüm hizmetin performansını tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9033a-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="9033a-104">Performans İzleyicisi (Perfmon. exe `ServiceModelService 4.0.0.0` ) ile görüntülenirken Performans nesnesi altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="9033a-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="9033a-105">Örnekler aşağıdaki model kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="9033a-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
> <span data-ttu-id="9033a-106">Performans sayacı örneğinin adının uzunluğu için bir sınır vardır.</span><span class="sxs-lookup"><span data-stu-id="9033a-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="9033a-107">Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aştığında, WCF örnek adının bir bölümünü bir karma değerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="9033a-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9033a-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9033a-108">See also</span></span>

- [<span data-ttu-id="9033a-109">Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="9033a-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
