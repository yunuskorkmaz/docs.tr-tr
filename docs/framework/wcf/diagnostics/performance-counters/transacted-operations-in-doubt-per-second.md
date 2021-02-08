---
description: Hakkında daha fazla bilgi için bkz. şüpheli Işlemler/saniye
title: Şüpheli Uygulanan İşlem/Saniye
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: e4f8b8c9db1c92ea4348763cdc4a633f058dbaf2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771099"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="cf8f6-103">Şüpheli Uygulanan İşlem/Saniye</span><span class="sxs-lookup"><span data-stu-id="cf8f6-103">Transacted Operations In Doubt Per Second</span></span>

<span data-ttu-id="cf8f6-104">Sayaç adı: saniyede şüpheli Işlem sayısı.</span><span class="sxs-lookup"><span data-stu-id="cf8f6-104">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cf8f6-105">Description</span><span class="sxs-lookup"><span data-stu-id="cf8f6-105">Description</span></span>  

 <span data-ttu-id="cf8f6-106">Saniye içinde bu hizmette şüpheli bir sonuca sahip işlem işlemlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="cf8f6-106">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="cf8f6-107">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="cf8f6-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="cf8f6-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="cf8f6-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
