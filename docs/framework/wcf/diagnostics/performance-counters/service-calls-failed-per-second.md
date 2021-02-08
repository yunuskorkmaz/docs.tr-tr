---
description: 'Şu konuda daha fazla bilgi edinin: hizmet: başarısız çağrı/saniye'
title: 'Hizmet: Saniyede Başarısız Olan Çağrı'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: b271d5076d0f0c89c4d33b124e0184584795466a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803366"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="8fc20-103">Hizmet: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="8fc20-103">Service: Calls Failed Per Second</span></span>

<span data-ttu-id="8fc20-104">Sayaç adı: saniye başına başarısız çağrı.</span><span class="sxs-lookup"><span data-stu-id="8fc20-104">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8fc20-105">Description</span><span class="sxs-lookup"><span data-stu-id="8fc20-105">Description</span></span>  

 <span data-ttu-id="8fc20-106">İşlenmemiş özel durumlara sahip ve bu hizmet tarafından bir saniyede alınan çağrıların sayısı.</span><span class="sxs-lookup"><span data-stu-id="8fc20-106">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="8fc20-107">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="8fc20-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="8fc20-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="8fc20-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="8fc20-109">Yönetilen kodda, hata koşulları oluştuğunda özel durumlar oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8fc20-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="8fc20-110">Yönetilen kodda, hata koşulları oluştuğunda özel durumlar oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8fc20-110">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="8fc20-111">Bu hizmette işlenmeyen bir özel durum olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="8fc20-111">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc20-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fc20-112">See also</span></span>

- [<span data-ttu-id="8fc20-113">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="8fc20-113">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
