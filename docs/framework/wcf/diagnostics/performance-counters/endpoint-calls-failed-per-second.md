---
title: 'Uç noktası: Saniyede Başarısız Olan Çağrı'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 03fbdd83246fa811424f445823f705a3bef5697a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608043"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="4ee8d-102">Uç noktası: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="4ee8d-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="4ee8d-103">Sayaç adı: Saniye başına başarısız olan çağrılar.</span><span class="sxs-lookup"><span data-stu-id="4ee8d-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4ee8d-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ee8d-104">Description</span></span>  
 <span data-ttu-id="4ee8d-105">Bu bitiş noktası tarafından saniyede alınan ve yakalanamayan özel durumları çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="4ee8d-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="4ee8d-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="4ee8d-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="4ee8d-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="4ee8d-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="4ee8d-108">Var olan her zaman işlenmeyen bir özel durum Bu uç noktada Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="4ee8d-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ee8d-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ee8d-109">See also</span></span>
- [<span data-ttu-id="4ee8d-110">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="4ee8d-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
