---
title: 'Uç Noktası: Saniyede Başarısız Olan Çağrı'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 97e887bd04cd7a755ce38914ace6de39ac871687
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545722"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="6a731-102">Uç Noktası: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="6a731-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="6a731-103">Sayaç adı: saniye başına başarısız çağrı.</span><span class="sxs-lookup"><span data-stu-id="6a731-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6a731-104">Description</span><span class="sxs-lookup"><span data-stu-id="6a731-104">Description</span></span>  
 <span data-ttu-id="6a731-105">İşlenmemiş özel durumları olan ve bu bitiş noktası tarafından bir saniyede alınan çağrıların sayısı.</span><span class="sxs-lookup"><span data-stu-id="6a731-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="6a731-106">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="6a731-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="6a731-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="6a731-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="6a731-108">Bu uç noktada işlenmeyen bir özel durum olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="6a731-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a731-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a731-109">See also</span></span>

- [<span data-ttu-id="6a731-110">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="6a731-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
