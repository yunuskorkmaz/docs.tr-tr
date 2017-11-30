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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ce34295e5ec318bcff9887765c46bde59066ab4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="9ee81-102">Saniyede Kuyruğa Alınan Zehirli İleti</span><span class="sxs-lookup"><span data-stu-id="9ee81-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="9ee81-103">Sayaç adı: Sıraya alınmış zarar iletileri saniyede.</span><span class="sxs-lookup"><span data-stu-id="9ee81-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9ee81-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ee81-104">Description</span></span>  
 <span data-ttu-id="9ee81-105">Bir saniyede sıraya alınan aktarım sırasında bu hizmet tarafından zarar görmüş işaretlenmiş iletilerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="9ee81-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="9ee81-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="9ee81-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9ee81-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="9ee81-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
