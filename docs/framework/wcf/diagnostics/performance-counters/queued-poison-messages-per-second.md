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
ms.openlocfilehash: 2811cbcca7d4e11465191e5d25b820b4a7b15e4d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="f2724-102">Saniyede Kuyruğa Alınan Zehirli İleti</span><span class="sxs-lookup"><span data-stu-id="f2724-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="f2724-103">Sayaç adı: Sıraya alınmış zarar iletileri saniyede.</span><span class="sxs-lookup"><span data-stu-id="f2724-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f2724-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2724-104">Description</span></span>  
 <span data-ttu-id="f2724-105">Bir saniyede sıraya alınan aktarım sırasında bu hizmet tarafından zarar görmüş işaretlenmiş iletilerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="f2724-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="f2724-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="f2724-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f2724-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="f2724-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
