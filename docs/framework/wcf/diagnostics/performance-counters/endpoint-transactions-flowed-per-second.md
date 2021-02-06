---
description: 'Şu konuda daha fazla bilgi edinin: uç nokta: saniye başına aktarılan Işlem'
title: 'Uç noktası: Saniyede Akışı Yapılan İşlem'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 96a122b97bce703b0a0e00c6e74f72c980253652
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655363"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="7c02f-103">Uç noktası: Saniyede Akışı Yapılan İşlem</span><span class="sxs-lookup"><span data-stu-id="7c02f-103">Endpoint: Transactions Flowed Per Second</span></span>

<span data-ttu-id="7c02f-104">Sayaç adı: saniye başına akan Işlem.</span><span class="sxs-lookup"><span data-stu-id="7c02f-104">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7c02f-105">Description</span><span class="sxs-lookup"><span data-stu-id="7c02f-105">Description</span></span>  

 <span data-ttu-id="7c02f-106">Bu bitiş noktasındaki işlemlere aktarılan işlem sayısı (saniye).</span><span class="sxs-lookup"><span data-stu-id="7c02f-106">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="7c02f-107">Bu sayaç, uç noktaya gönderilen bir iletide bir işlem KIMLIĞI olduğunda artırılır.</span><span class="sxs-lookup"><span data-stu-id="7c02f-107">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="7c02f-108">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="7c02f-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="7c02f-109">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="7c02f-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
