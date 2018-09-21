---
title: Şüpheli Uygulanan İşlem/Saniye
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: f7365c4e5f03711129916c8c6964f7e25e9b553e
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46493465"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="e83e2-102">Şüpheli Uygulanan İşlem/Saniye</span><span class="sxs-lookup"><span data-stu-id="e83e2-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="e83e2-103">Sayaç adı: Şüpheli uygulanan işlem / saniye.</span><span class="sxs-lookup"><span data-stu-id="e83e2-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e83e2-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e83e2-104">Description</span></span>  
 <span data-ttu-id="e83e2-105">Bir saniye içinde şüpheli sonucu bu hizmette işlem işlemlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="e83e2-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="e83e2-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="e83e2-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e83e2-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="e83e2-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
