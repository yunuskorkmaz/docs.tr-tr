---
title: Saniyede Başarısız Olan Çağrı
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: 8f2337d5ea3eb696c7be5b25d01396676dae2458
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554123"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="33e27-102">Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="33e27-102">Calls Failed Per Second</span></span>
<span data-ttu-id="33e27-103">Sayaç adı: başarısız çağrı/saniye</span><span class="sxs-lookup"><span data-stu-id="33e27-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="33e27-104">Description</span><span class="sxs-lookup"><span data-stu-id="33e27-104">Description</span></span>  
 <span data-ttu-id="33e27-105">Saniye içinde bu işlemdeki işlenmemiş özel durumları olan çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="33e27-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="33e27-106">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="33e27-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="33e27-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="33e27-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="33e27-108">Bu işlemde işlenmeyen bir özel durum olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="33e27-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e27-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33e27-109">See also</span></span>

- [<span data-ttu-id="33e27-110">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="33e27-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
