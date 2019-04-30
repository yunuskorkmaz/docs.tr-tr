---
title: Şüpheli Uygulanan İşlem/Saniye
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: f7365c4e5f03711129916c8c6964f7e25e9b553e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766343"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="8f4b8-102">Şüpheli Uygulanan İşlem/Saniye</span><span class="sxs-lookup"><span data-stu-id="8f4b8-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="8f4b8-103">Sayaç adı: Saniyede şüpheli uygulanan işlemler.</span><span class="sxs-lookup"><span data-stu-id="8f4b8-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8f4b8-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f4b8-104">Description</span></span>  
 <span data-ttu-id="8f4b8-105">Bir saniye içinde şüpheli sonucu bu hizmette işlem işlemlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="8f4b8-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="8f4b8-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="8f4b8-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="8f4b8-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="8f4b8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
