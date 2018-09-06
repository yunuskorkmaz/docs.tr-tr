---
title: Saniyede Başarısız Olan Çağrı
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: ccb5908e9036650e3f21a9496649c8090c2e47b2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736328"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="054c1-102">Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="054c1-102">Calls Failed Per Second</span></span>
<span data-ttu-id="054c1-103">Sayaç adı: Saniyede başarısız olan çağrılar</span><span class="sxs-lookup"><span data-stu-id="054c1-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="054c1-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="054c1-104">Description</span></span>  
 <span data-ttu-id="054c1-105">Bu işlem bir saniye içinde işlenmeyen özel durumları ile çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="054c1-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="054c1-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="054c1-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="054c1-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="054c1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="054c1-108">Bu sayaç artan kaydedilir bu işlemi işlenmeyen bir özel durum yoktur.</span><span class="sxs-lookup"><span data-stu-id="054c1-108">This counter is incremented everytime there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="054c1-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="054c1-109">See Also</span></span>  
 [<span data-ttu-id="054c1-110">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="054c1-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
