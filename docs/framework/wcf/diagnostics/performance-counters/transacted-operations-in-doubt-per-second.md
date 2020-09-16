---
title: Şüpheli Uygulanan İşlem/Saniye
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: 59186b1fc113bb87264a8b946cfee2719ff50b62
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550605"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="5277f-102">Şüpheli Uygulanan İşlem/Saniye</span><span class="sxs-lookup"><span data-stu-id="5277f-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="5277f-103">Sayaç adı: saniyede şüpheli Işlem sayısı.</span><span class="sxs-lookup"><span data-stu-id="5277f-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5277f-104">Description</span><span class="sxs-lookup"><span data-stu-id="5277f-104">Description</span></span>  
 <span data-ttu-id="5277f-105">Saniye içinde bu hizmette şüpheli bir sonuca sahip işlem işlemlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="5277f-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="5277f-106">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="5277f-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5277f-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="5277f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
