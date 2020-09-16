---
title: 'Hizmet: Saniyede Başarısız Olan Çağrı'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 5629c55cba6f21de24a1de7e8d38a9c08fcf4fb1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559115"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="365d4-102">Hizmet: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="365d4-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="365d4-103">Sayaç adı: saniye başına başarısız çağrı.</span><span class="sxs-lookup"><span data-stu-id="365d4-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="365d4-104">Description</span><span class="sxs-lookup"><span data-stu-id="365d4-104">Description</span></span>  
 <span data-ttu-id="365d4-105">İşlenmemiş özel durumlara sahip ve bu hizmet tarafından bir saniyede alınan çağrıların sayısı.</span><span class="sxs-lookup"><span data-stu-id="365d4-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="365d4-106">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="365d4-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="365d4-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="365d4-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="365d4-108">Yönetilen kodda, hata koşulları oluştuğunda özel durumlar oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="365d4-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="365d4-109">Yönetilen kodda, hata koşulları oluştuğunda özel durumlar oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="365d4-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="365d4-110">Bu hizmette işlenmeyen bir özel durum olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="365d4-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="365d4-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="365d4-111">See also</span></span>

- [<span data-ttu-id="365d4-112">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="365d4-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
