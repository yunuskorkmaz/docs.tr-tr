---
title: 'Uç noktası: Saniyede Akışı Yapılan İşlem'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 39458dcb6ac033fd5084b5f2e760e0e26c345da7
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163559"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="fdcb5-102">Uç noktası: Saniyede Akışı Yapılan İşlem</span><span class="sxs-lookup"><span data-stu-id="fdcb5-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="fdcb5-103">Sayaç adı: saniye başına akan Işlem.</span><span class="sxs-lookup"><span data-stu-id="fdcb5-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fdcb5-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fdcb5-104">Description</span></span>  
 <span data-ttu-id="fdcb5-105">Bu bitiş noktasındaki işlemlere aktarılan işlem sayısı (saniye).</span><span class="sxs-lookup"><span data-stu-id="fdcb5-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="fdcb5-106">Bu sayaç, uç noktaya gönderilen bir iletide bir işlem KIMLIĞI olduğunda artırılır.</span><span class="sxs-lookup"><span data-stu-id="fdcb5-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="fdcb5-107">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="fdcb5-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fdcb5-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="fdcb5-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
