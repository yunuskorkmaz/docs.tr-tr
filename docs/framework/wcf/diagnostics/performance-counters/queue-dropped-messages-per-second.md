---
title: "Saniyede Kuyruğa Alınan Bırakılmış İleti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8512c757f7a18172b267fe7d3469b1a2749818aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="e9808-102">Saniyede Kuyruğa Alınan Bırakılmış İleti</span><span class="sxs-lookup"><span data-stu-id="e9808-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="e9808-103">Sayaç adı: Saniye başına bırakılan iletileri kuyruğa alındı.</span><span class="sxs-lookup"><span data-stu-id="e9808-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e9808-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9808-104">Description</span></span>  
 <span data-ttu-id="e9808-105">Sıraya alınan aktarım sırasında bu hizmet tarafından bir saniyede bırakılan ileti sayısı.</span><span class="sxs-lookup"><span data-stu-id="e9808-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="e9808-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="e9808-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e9808-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="e9808-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
