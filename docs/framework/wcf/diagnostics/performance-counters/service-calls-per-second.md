---
title: 'Hizmet: Saniye Başına Çağrı'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: be5d77169a71d6f44205a1150da5239eceff7d9c
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163910"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="fefb2-102">Hizmet: Saniye Başına Çağrı</span><span class="sxs-lookup"><span data-stu-id="fefb2-102">Service: Calls Per Second</span></span>
<span data-ttu-id="fefb2-103">Sayaç adı: saniye başına çağrı.</span><span class="sxs-lookup"><span data-stu-id="fefb2-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fefb2-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fefb2-104">Description</span></span>  
 <span data-ttu-id="fefb2-105">Bu hizmete saniye içinde yapılan çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="fefb2-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="fefb2-106">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="fefb2-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fefb2-107">(N 1-N 0)/((D 1-D 0)/F) pay (N) son örnekleme aralığı sırasında gerçekleştirilen işlem sayısını temsil ediyorsa, payda (D) son örnekleme aralığı sırasında geçen işaret sayısını temsil eder ve F, Tick 'lerin sıklığıdır.</span><span class="sxs-lookup"><span data-stu-id="fefb2-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
