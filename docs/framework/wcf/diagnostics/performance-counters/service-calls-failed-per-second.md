---
title: 'Hizmet: Saniyede Başarısız Olan Çağrı'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: d87d5f06d0c9a3849ec80a3d1c7badefde7cf372
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167498"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="254d8-102">Hizmet: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="254d8-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="254d8-103">Sayaç adı: Saniye başına başarısız olan çağrılar.</span><span class="sxs-lookup"><span data-stu-id="254d8-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="254d8-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="254d8-104">Description</span></span>  
 <span data-ttu-id="254d8-105">Yakalanamayan özel durumları ve bu hizmet tarafından bir saniyede alınan çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="254d8-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="254d8-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="254d8-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="254d8-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="254d8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="254d8-108">Hata koşullarını ortaya çıktığında yönetilen kodda özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="254d8-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="254d8-109">Hata koşullarını ortaya çıktığında yönetilen kodda özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="254d8-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="254d8-110">Var olan her zaman bu hizmeti içinde işlenmeyen bir özel Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="254d8-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="254d8-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="254d8-111">See also</span></span>

- [<span data-ttu-id="254d8-112">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="254d8-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
