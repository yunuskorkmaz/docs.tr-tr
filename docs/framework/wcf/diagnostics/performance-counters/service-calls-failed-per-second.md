---
title: 'Hizmet: Saniyede Başarısız Olan Çağrı'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: a043cf30fa67707aca3edf50cf23372ade5e5a42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559898"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="5e0ff-102">Hizmet: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="5e0ff-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="5e0ff-103">Sayaç adı: Saniye başına başarısız olan çağrılar.</span><span class="sxs-lookup"><span data-stu-id="5e0ff-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5e0ff-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e0ff-104">Description</span></span>  
 <span data-ttu-id="5e0ff-105">Yakalanamayan özel durumları ve bu hizmet tarafından bir saniyede alınan çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="5e0ff-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="5e0ff-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="5e0ff-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5e0ff-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="5e0ff-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="5e0ff-108">Hata koşullarını ortaya çıktığında yönetilen kodda özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="5e0ff-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="5e0ff-109">Hata koşullarını ortaya çıktığında yönetilen kodda özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="5e0ff-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="5e0ff-110">Var olan her zaman bu hizmeti içinde işlenmeyen bir özel Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="5e0ff-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e0ff-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e0ff-111">See also</span></span>
- [<span data-ttu-id="5e0ff-112">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="5e0ff-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
