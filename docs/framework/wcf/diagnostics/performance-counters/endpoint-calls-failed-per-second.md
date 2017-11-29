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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5da436c5e8159ff922c36172490a28e854bbee8b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="38d4c-102">Uç Noktası: Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="38d4c-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="38d4c-103">Sayaç adı: Saniye başına çağrı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="38d4c-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="38d4c-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38d4c-104">Description</span></span>  
 <span data-ttu-id="38d4c-105">Özel durum işlenmemiş ve bu bitiş noktası tarafından bir saniyede alınan çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="38d4c-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="38d4c-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="38d4c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="38d4c-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="38d4c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="38d4c-108">Olduğundan her zaman bu uç noktada işlenmeyen bir özel durum, bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="38d4c-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d4c-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38d4c-109">See Also</span></span>  
 [<span data-ttu-id="38d4c-110">Belirtme ve sözleşme ve hizmetlerde hataları işleme</span><span class="sxs-lookup"><span data-stu-id="38d4c-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
