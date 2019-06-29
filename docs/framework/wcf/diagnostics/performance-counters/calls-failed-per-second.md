---
title: Saniyede Başarısız Olan Çağrı
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: aa8cd4c2d9f642b525b2b9ccb931c4f2101a5129
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421782"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="64293-102">Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="64293-102">Calls Failed Per Second</span></span>
<span data-ttu-id="64293-103">Sayaç adı: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="64293-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="64293-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64293-104">Description</span></span>  
 <span data-ttu-id="64293-105">Bu işlem bir saniye içinde işlenmeyen özel durumları ile çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="64293-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="64293-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="64293-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="64293-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="64293-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="64293-108">Var olan her zaman bu işlem içinde işlenmeyen bir özel Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="64293-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64293-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64293-109">See also</span></span>

- [<span data-ttu-id="64293-110">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="64293-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
