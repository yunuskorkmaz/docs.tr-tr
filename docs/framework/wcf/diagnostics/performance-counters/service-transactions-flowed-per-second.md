---
title: 'Hizmet: Saniyede Akışı Yapılan İşlem'
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: 1151117c8537d4a8eaa4de60d14e314b55ce82d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474850"
---
# <a name="service-transactions-flowed-per-second"></a><span data-ttu-id="dca5e-102">Hizmet: Saniyede Akışı Yapılan İşlem</span><span class="sxs-lookup"><span data-stu-id="dca5e-102">Service: Transactions Flowed Per Second</span></span>
<span data-ttu-id="dca5e-103">Sayaç adı: Saniyede akışı yapılan işlemler.</span><span class="sxs-lookup"><span data-stu-id="dca5e-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dca5e-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dca5e-104">Description</span></span>  
 <span data-ttu-id="dca5e-105">İşlem sayısı bu hizmet işlemleri için bir saniyede akışı yapılan işlem.</span><span class="sxs-lookup"><span data-stu-id="dca5e-105">Number of transactions flowed to operations in this service in a second.</span></span>  
  
 <span data-ttu-id="dca5e-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="dca5e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="dca5e-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="dca5e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
