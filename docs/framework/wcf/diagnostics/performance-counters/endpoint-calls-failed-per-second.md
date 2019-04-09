---
title: 'Uç noktası: Saniyede Başarısız Olan Çağrı'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 52419f45adde768d19d6b46642d52ad0a1844197
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100034"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="79dd8-102">Uç noktası: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="79dd8-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="79dd8-103">Sayaç adı: Saniye başına başarısız olan çağrılar.</span><span class="sxs-lookup"><span data-stu-id="79dd8-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="79dd8-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79dd8-104">Description</span></span>  
 <span data-ttu-id="79dd8-105">Bu bitiş noktası tarafından saniyede alınan ve yakalanamayan özel durumları çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="79dd8-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="79dd8-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="79dd8-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="79dd8-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="79dd8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="79dd8-108">Var olan her zaman işlenmeyen bir özel durum Bu uç noktada Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="79dd8-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79dd8-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79dd8-109">See also</span></span>

- [<span data-ttu-id="79dd8-110">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="79dd8-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
