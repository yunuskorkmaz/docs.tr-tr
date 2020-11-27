---
title: Saniyede Başarısız Olan Çağrı
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: d3eafc4b31f0e62093a972b7c9f2325a3648d21b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285466"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="ea679-102">Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="ea679-102">Calls Failed Per Second</span></span>

<span data-ttu-id="ea679-103">Sayaç adı: başarısız çağrı/saniye</span><span class="sxs-lookup"><span data-stu-id="ea679-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="ea679-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea679-104">Description</span></span>  

 <span data-ttu-id="ea679-105">Saniye içinde bu işlemdeki işlenmemiş özel durumları olan çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="ea679-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="ea679-106">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="ea679-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ea679-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="ea679-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="ea679-108">Bu işlemde işlenmeyen bir özel durum olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="ea679-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea679-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea679-109">See also</span></span>

- [<span data-ttu-id="ea679-110">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="ea679-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
