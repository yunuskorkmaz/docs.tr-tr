---
description: 'Hakkında daha fazla bilgi edinin: Saniyedeki başarısız olan çağrılar'
title: Saniyede Başarısız Olan Çağrı
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: 3961754eb73743a1213922f7c9e1bd164334cd6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759724"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="e4f56-103">Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="e4f56-103">Calls Failed Per Second</span></span>

<span data-ttu-id="e4f56-104">Sayaç adı: başarısız çağrı/saniye</span><span class="sxs-lookup"><span data-stu-id="e4f56-104">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="e4f56-105">Description</span><span class="sxs-lookup"><span data-stu-id="e4f56-105">Description</span></span>  

 <span data-ttu-id="e4f56-106">Saniye içinde bu işlemdeki işlenmemiş özel durumları olan çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="e4f56-106">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="e4f56-107">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="e4f56-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e4f56-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="e4f56-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="e4f56-109">Bu işlemde işlenmeyen bir özel durum olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="e4f56-109">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f56-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4f56-110">See also</span></span>

- [<span data-ttu-id="e4f56-111">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="e4f56-111">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
