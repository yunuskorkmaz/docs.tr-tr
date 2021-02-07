---
description: 'Şu konuda daha fazla bilgi edinin: hizmet: çağrı/saniye'
title: 'Hizmet: Saniye Başına Çağrı'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: f6e21f5f1c7a0d5d4ceeb11f954ebbc95f66a3ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99744038"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="afe26-103">Hizmet: Saniye Başına Çağrı</span><span class="sxs-lookup"><span data-stu-id="afe26-103">Service: Calls Per Second</span></span>

<span data-ttu-id="afe26-104">Sayaç adı: saniye başına çağrı.</span><span class="sxs-lookup"><span data-stu-id="afe26-104">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="afe26-105">Description</span><span class="sxs-lookup"><span data-stu-id="afe26-105">Description</span></span>  

 <span data-ttu-id="afe26-106">Bu hizmete saniye içinde yapılan çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="afe26-106">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="afe26-107">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="afe26-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="afe26-108">(N 1-N 0)/((D 1-D 0)/F) pay (N) son örnekleme aralığı sırasında gerçekleştirilen işlem sayısını temsil ediyorsa, payda (D) son örnekleme aralığı sırasında geçen işaret sayısını temsil eder ve F, Tick 'lerin sıklığıdır.</span><span class="sxs-lookup"><span data-stu-id="afe26-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
