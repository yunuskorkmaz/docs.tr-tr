---
title: Saniyede Kuyruğa Alınan Zehirli İleti
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: 6407cce120f5d534f88a12591ea2ad09bb5130d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473265"
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="a6941-102">Saniyede Kuyruğa Alınan Zehirli İleti</span><span class="sxs-lookup"><span data-stu-id="a6941-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="a6941-103">Sayaç adı: Sıraya alınmış zarar iletileri saniyede.</span><span class="sxs-lookup"><span data-stu-id="a6941-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a6941-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6941-104">Description</span></span>  
 <span data-ttu-id="a6941-105">Bir saniyede sıraya alınan aktarım sırasında bu hizmet tarafından zarar görmüş işaretlenmiş iletilerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="a6941-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="a6941-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="a6941-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="a6941-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="a6941-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
