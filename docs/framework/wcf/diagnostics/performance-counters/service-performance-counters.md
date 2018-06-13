---
title: Hizmet Performansı Sayaçları
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: bdc68fd2b629c538c097dab4e1cf3f89b7f3a091
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810193"
---
# <a name="service-performance-counters"></a><span data-ttu-id="4f9a0-102">Hizmet Performansı Sayaçları</span><span class="sxs-lookup"><span data-stu-id="4f9a0-102">Service Performance Counters</span></span>
<span data-ttu-id="4f9a0-103">Hizmeti performans sayaçları hizmet davranışı bir bütün olarak ölçmek ve tüm hizmet performansını tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4f9a0-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="4f9a0-104">Altında bulunabilir `ServiceModelService 4.0.0.0` Performans İzleyicisi (Perfmon.exe) görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4f9a0-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="4f9a0-105">Örnekleri şu biçimi kullanarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="4f9a0-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="4f9a0-106">Bir performans sayacı örneğinin adının uzunluğu bir sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="4f9a0-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="4f9a0-107">Bir Windows Communication Foundation (WCF) sayaç örneği adı uzunluk üst sınırını aşarsa, WCF örnek adının bir kısmını karma değeri ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="4f9a0-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f9a0-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f9a0-108">See Also</span></span>  
 [<span data-ttu-id="4f9a0-109">Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="4f9a0-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
