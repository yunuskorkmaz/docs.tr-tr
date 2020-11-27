---
title: Hizmet Performansı Sayaçları
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: f3e3a798bf04f24aaea03b5d70762d52b67a82f0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252835"
---
# <a name="service-performance-counters"></a><span data-ttu-id="11330-102">Hizmet Performansı Sayaçları</span><span class="sxs-lookup"><span data-stu-id="11330-102">Service Performance Counters</span></span>

<span data-ttu-id="11330-103">Hizmet performans sayaçları, hizmet davranışını bir bütün olarak ölçer ve tüm hizmetin performansını tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="11330-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="11330-104">Performans `ServiceModelService 4.0.0.0` İzleyicisi (Perfmon.exe) ile görüntülenirken Performans nesnesi altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="11330-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="11330-105">Örnekler aşağıdaki model kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="11330-105">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> <span data-ttu-id="11330-106">Performans sayacı örneğinin adının uzunluğu için bir sınır vardır.</span><span class="sxs-lookup"><span data-stu-id="11330-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="11330-107">Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aştığında, WCF örnek adının bir bölümünü bir karma değerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="11330-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11330-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11330-108">See also</span></span>

- [<span data-ttu-id="11330-109">Performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="11330-109">Performance Counters</span></span>](index.md)
