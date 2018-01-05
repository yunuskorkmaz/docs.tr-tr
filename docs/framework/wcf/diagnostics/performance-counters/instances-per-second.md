---
title: "Saniye Başına Örnek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74579397-1058-4278-80cf-2d00854a480f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 40eb52dcc196f4c4a89508246af1c129b5eadb8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="instances-per-second"></a><span data-ttu-id="871fb-102">Saniye Başına Örnek</span><span class="sxs-lookup"><span data-stu-id="871fb-102">Instances Per Second</span></span>
<span data-ttu-id="871fb-103">Sayaç adı: Saniye başına oluşturulan örnekleri.</span><span class="sxs-lookup"><span data-stu-id="871fb-103">Counter Name: Instances Created Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="871fb-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="871fb-104">Description</span></span>  
 <span data-ttu-id="871fb-105">Hizmet örneklerinin bir saniye içinde oluşturulan toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="871fb-105">Total number of service instances created in a second.</span></span>  
  
 <span data-ttu-id="871fb-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="871fb-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="871fb-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="871fb-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
