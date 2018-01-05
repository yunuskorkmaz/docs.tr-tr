---
title: "Uç Noktası: Saniyede Başarısız Olan Çağrı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a6aaf1e504909805a542840fe92a6591c9083d8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="5a462-102">Uç Noktası: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="5a462-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="5a462-103">Sayaç adı: Saniye başına çağrı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="5a462-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5a462-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a462-104">Description</span></span>  
 <span data-ttu-id="5a462-105">Özel durum işlenmemiş ve bu bitiş noktası tarafından bir saniyede alınan çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="5a462-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="5a462-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="5a462-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5a462-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="5a462-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="5a462-108">Olduğundan her zaman bu uç noktada işlenmeyen bir özel durum, bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="5a462-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a462-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a462-109">See Also</span></span>  
 [<span data-ttu-id="5a462-110">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="5a462-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
