---
title: 'Hizmet: Çağrı/saniye'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 5189a78e2655707d165f187e06ac9a60d055eac0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773371"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="15033-102">Hizmet: Çağrı/saniye</span><span class="sxs-lookup"><span data-stu-id="15033-102">Service: Calls Per Second</span></span>
<span data-ttu-id="15033-103">Sayaç adı: Saniyede çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="15033-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="15033-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15033-104">Description</span></span>  
 <span data-ttu-id="15033-105">Bu hizmete bir saniye içinde çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="15033-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="15033-106">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="15033-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="15033-107">(1 - N 0 N) / ((1 D -D 0) / F) (N) pay tıklarının sayısını geçen son örnek zaman aralığı boyunca paydası (D) temsil son örnek aralığı sırasında gerçekleştirilen işlemlerin sayısını temsil eder ve F işaretleri sıklığını olduğu yerde.</span><span class="sxs-lookup"><span data-stu-id="15033-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
