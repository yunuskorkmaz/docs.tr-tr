---
title: Saniyede Kuyruğa Alınan Bırakılmış İleti
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: f15b2db08ac4486377189a1533b653260d79024a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418254"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="15d4a-102">Saniyede Kuyruğa Alınan Bırakılmış İleti</span><span class="sxs-lookup"><span data-stu-id="15d4a-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="15d4a-103">Sayaç adı: Saniye başına bırakılan iletileri kuyruğa alındı.</span><span class="sxs-lookup"><span data-stu-id="15d4a-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="15d4a-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15d4a-104">Description</span></span>  
 <span data-ttu-id="15d4a-105">Bir saniyede sıraya alınan aktarım sırasında bu hizmeti tarafından bırakılan ileti sayısı.</span><span class="sxs-lookup"><span data-stu-id="15d4a-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="15d4a-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="15d4a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="15d4a-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="15d4a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
