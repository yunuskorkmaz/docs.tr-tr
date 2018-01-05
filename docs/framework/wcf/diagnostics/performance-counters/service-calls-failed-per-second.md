---
title: "Hizmet: Saniyede Başarısız Olan Çağrı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 632c81b6ffd84202b7609dccb89887af01ae706e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="3d385-102">Hizmet: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="3d385-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="3d385-103">Sayaç adı: Saniye başına çağrı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="3d385-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3d385-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d385-104">Description</span></span>  
 <span data-ttu-id="3d385-105">Özel durum işlenmemiş ve bu hizmet tarafından bir saniyede alınan çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="3d385-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="3d385-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="3d385-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="3d385-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="3d385-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="3d385-108">Hata koşullarını ortaya çıktığında yönetilen kodda özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="3d385-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="3d385-109">Hata koşullarını ortaya çıktığında yönetilen kodda özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="3d385-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="3d385-110">Olduğundan her zaman bu hizmeti işlenmeyen bir özel durum, bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="3d385-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d385-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d385-111">See Also</span></span>  
 [<span data-ttu-id="3d385-112">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="3d385-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
