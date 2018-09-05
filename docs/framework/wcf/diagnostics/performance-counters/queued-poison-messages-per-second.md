---
title: Saniyede Kuyruğa Alınan Zehirli İleti
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: d4c921b105dfd1c1a364d2c86f54ab920078dd4a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509345"
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="efb3e-102">Saniyede Kuyruğa Alınan Zehirli İleti</span><span class="sxs-lookup"><span data-stu-id="efb3e-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="efb3e-103">Sayaç adı: Sıraya alınmış zehirli iletiler / saniye.</span><span class="sxs-lookup"><span data-stu-id="efb3e-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="efb3e-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efb3e-104">Description</span></span>  
 <span data-ttu-id="efb3e-105">Bir saniyede sıraya alınan aktarım sırasında bu hizmeti tarafından zarar görmüş işaretlenmiş iletilerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="efb3e-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="efb3e-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="efb3e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="efb3e-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="efb3e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
