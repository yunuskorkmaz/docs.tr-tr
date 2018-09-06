---
title: 'Uç Noktası: Saniyede Başarısız Olan Çağrı'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: fa4fc1d8a875557f1da9e54e7a05eb012e7c221c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856354"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="e2bba-102">Uç Noktası: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="e2bba-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="e2bba-103">Sayaç adı: Saniye başına çağrı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="e2bba-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e2bba-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2bba-104">Description</span></span>  
 <span data-ttu-id="e2bba-105">Bu bitiş noktası tarafından saniyede alınan ve yakalanamayan özel durumları çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="e2bba-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="e2bba-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="e2bba-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e2bba-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="e2bba-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="e2bba-108">Var olan her zaman işlenmeyen bir özel durum Bu uç noktada Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="e2bba-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2bba-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2bba-109">See Also</span></span>  
 [<span data-ttu-id="e2bba-110">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="e2bba-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
