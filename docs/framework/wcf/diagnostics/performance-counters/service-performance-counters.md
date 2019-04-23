---
title: Hizmet Performansı Sayaçları
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: dc31e05f82f232095f6560c8fdd9bf75c040e2ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210418"
---
# <a name="service-performance-counters"></a><span data-ttu-id="04b8f-102">Hizmet Performansı Sayaçları</span><span class="sxs-lookup"><span data-stu-id="04b8f-102">Service Performance Counters</span></span>
<span data-ttu-id="04b8f-103">Hizmeti performans sayaçları, hizmet davranışı bir bütün olarak ölçmek ve tüm servis performansını tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="04b8f-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="04b8f-104">Altında bulunabilir `ServiceModelService 4.0.0.0` Performans İzleyicisi (Perfmon.exe) görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="04b8f-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="04b8f-105">Örnekleri aşağıdaki deseni kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="04b8f-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="04b8f-106">Bir performans sayacı örneğinin adının uzunluğu üzerinde bir sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="04b8f-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="04b8f-107">Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aşıyor, WCF örnek adının bir kısmını bir karma değer ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="04b8f-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b8f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04b8f-108">See also</span></span>

- [<span data-ttu-id="04b8f-109">Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="04b8f-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
