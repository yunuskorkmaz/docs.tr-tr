---
description: 'Şu konuda daha fazla bilgi edinin: uç nokta: başarısız çağrı/saniye'
title: 'Uç Noktası: Saniyede Başarısız Olan Çağrı'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 262f0fdf0750e8fdb179d41d1a99788784270023
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759646"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="402a6-103">Uç Noktası: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="402a6-103">Endpoint: Calls Failed Per Second</span></span>

<span data-ttu-id="402a6-104">Sayaç adı: saniye başına başarısız çağrı.</span><span class="sxs-lookup"><span data-stu-id="402a6-104">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="402a6-105">Description</span><span class="sxs-lookup"><span data-stu-id="402a6-105">Description</span></span>  

 <span data-ttu-id="402a6-106">İşlenmemiş özel durumları olan ve bu bitiş noktası tarafından bir saniyede alınan çağrıların sayısı.</span><span class="sxs-lookup"><span data-stu-id="402a6-106">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="402a6-107">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="402a6-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="402a6-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="402a6-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="402a6-109">Bu uç noktada işlenmeyen bir özel durum olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="402a6-109">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="402a6-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="402a6-110">See also</span></span>

- [<span data-ttu-id="402a6-111">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="402a6-111">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
