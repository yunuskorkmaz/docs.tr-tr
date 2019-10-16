---
title: Hizmet Performansı Sayaçları
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 929ddcb2f271b7488270ea39e7a3a0037158c855
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320023"
---
# <a name="service-performance-counters"></a><span data-ttu-id="5bd25-102">Hizmet Performansı Sayaçları</span><span class="sxs-lookup"><span data-stu-id="5bd25-102">Service Performance Counters</span></span>
<span data-ttu-id="5bd25-103">Hizmet performans sayaçları, hizmet davranışını bir bütün olarak ölçer ve tüm hizmetin performansını tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5bd25-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="5bd25-104">Performans Izleyicisi (Perfmon. exe) ile görüntülenirken `ServiceModelService 4.0.0.0` performans nesnesi altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="5bd25-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="5bd25-105">Örnekler aşağıdaki model kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="5bd25-105">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> <span data-ttu-id="5bd25-106">Performans sayacı örneğinin adının uzunluğu için bir sınır vardır.</span><span class="sxs-lookup"><span data-stu-id="5bd25-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="5bd25-107">Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aştığında, WCF örnek adının bir bölümünü bir karma değerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5bd25-107">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd25-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bd25-108">See also</span></span>

- [<span data-ttu-id="5bd25-109">Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="5bd25-109">Performance Counters</span></span>](index.md)
