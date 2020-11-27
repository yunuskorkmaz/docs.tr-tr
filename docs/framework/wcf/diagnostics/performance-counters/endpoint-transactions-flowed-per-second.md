---
title: 'Uç noktası: Saniyede Akışı Yapılan İşlem'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: b814d7ca9e286426289c611b3a6bf5a52c1b2335
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256436"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="d02fb-102">Uç noktası: Saniyede Akışı Yapılan İşlem</span><span class="sxs-lookup"><span data-stu-id="d02fb-102">Endpoint: Transactions Flowed Per Second</span></span>

<span data-ttu-id="d02fb-103">Sayaç adı: saniye başına akan Işlem.</span><span class="sxs-lookup"><span data-stu-id="d02fb-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d02fb-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d02fb-104">Description</span></span>  

 <span data-ttu-id="d02fb-105">Bu bitiş noktasındaki işlemlere aktarılan işlem sayısı (saniye).</span><span class="sxs-lookup"><span data-stu-id="d02fb-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="d02fb-106">Bu sayaç, uç noktaya gönderilen bir iletide bir işlem KIMLIĞI olduğunda artırılır.</span><span class="sxs-lookup"><span data-stu-id="d02fb-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="d02fb-107">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="d02fb-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d02fb-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="d02fb-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
