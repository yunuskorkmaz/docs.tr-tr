---
title: 'Uç Noktası: Saniyede Başarısız Olan Çağrı'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: c0273fc90ad5702663862612f52f03c42f410b8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473500"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="1469c-102">Uç Noktası: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="1469c-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="1469c-103">Sayaç adı: Saniye başına çağrı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="1469c-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1469c-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1469c-104">Description</span></span>  
 <span data-ttu-id="1469c-105">Özel durum işlenmemiş ve bu bitiş noktası tarafından bir saniyede alınan çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1469c-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="1469c-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="1469c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="1469c-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="1469c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="1469c-108">Olduğundan her zaman bu uç noktada işlenmeyen bir özel durum, bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="1469c-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1469c-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1469c-109">See Also</span></span>  
 [<span data-ttu-id="1469c-110">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="1469c-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
