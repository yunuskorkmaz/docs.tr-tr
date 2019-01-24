---
title: Hizmet Performansı Sayaçları
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: bf0b12e6d4954c0a1392554d7269a7d539a77dc1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545601"
---
# <a name="service-performance-counters"></a><span data-ttu-id="be77b-102">Hizmet Performansı Sayaçları</span><span class="sxs-lookup"><span data-stu-id="be77b-102">Service Performance Counters</span></span>
<span data-ttu-id="be77b-103">Hizmeti performans sayaçları, hizmet davranışı bir bütün olarak ölçmek ve tüm servis performansını tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be77b-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="be77b-104">Altında bulunabilir `ServiceModelService 4.0.0.0` Performans İzleyicisi (Perfmon.exe) görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="be77b-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="be77b-105">Örnekleri aşağıdaki deseni kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="be77b-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="be77b-106">Bir performans sayacı örneğinin adının uzunluğu üzerinde bir sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="be77b-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="be77b-107">Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aşıyor, WCF örnek adının bir kısmını bir karma değer ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="be77b-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be77b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be77b-108">See also</span></span>
- [<span data-ttu-id="be77b-109">Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="be77b-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
