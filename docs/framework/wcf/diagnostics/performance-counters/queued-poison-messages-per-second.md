---
title: "Saniyede Kuyruğa Alınan Zehirli İleti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8f22d200834927204918324ced70ac02c3c669f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="20704-102">Saniyede Kuyruğa Alınan Zehirli İleti</span><span class="sxs-lookup"><span data-stu-id="20704-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="20704-103">Sayaç adı: Sıraya alınmış zarar iletileri saniyede.</span><span class="sxs-lookup"><span data-stu-id="20704-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="20704-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20704-104">Description</span></span>  
 <span data-ttu-id="20704-105">Bir saniyede sıraya alınan aktarım sırasında bu hizmet tarafından zarar görmüş işaretlenmiş iletilerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="20704-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="20704-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="20704-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="20704-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="20704-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
