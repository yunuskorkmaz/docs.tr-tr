---
title: "Şüpheli Uygulanan İşlem/Saniye"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7d42046d2d636d507aa682c349f29dcecedca657
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="d2937-102">Şüpheli Uygulanan İşlem/Saniye</span><span class="sxs-lookup"><span data-stu-id="d2937-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="d2937-103">Sayaç adı: Şüpheli uygulanan işlemler saniyede.</span><span class="sxs-lookup"><span data-stu-id="d2937-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d2937-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2937-104">Description</span></span>  
 <span data-ttu-id="d2937-105">Bu hizmet şüpheli sonucu ikinci bir işlem işlemleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="d2937-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="d2937-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="d2937-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d2937-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="d2937-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
