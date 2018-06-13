---
title: Saniyede Kuyruğa Alınan Reddedilen İleti
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: 31091c6c9dd04ecd7294f69f9611f25e401df724
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473451"
---
# <a name="queued-rejected-messages-per-second"></a><span data-ttu-id="fde0a-102">Saniyede Kuyruğa Alınan Reddedilen İleti</span><span class="sxs-lookup"><span data-stu-id="fde0a-102">Queued Rejected Messages Per Second</span></span>
<span data-ttu-id="fde0a-103">Sayaç adı: Saniyede reddedilen iletileri kuyruğa alındı.</span><span class="sxs-lookup"><span data-stu-id="fde0a-103">Counter Name: Queued Messages Rejected Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fde0a-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fde0a-104">Description</span></span>  
 <span data-ttu-id="fde0a-105">Bir saniyede sıraya alınan aktarım sırasında bu hizmet tarafından reddedilen ileti sayısı.</span><span class="sxs-lookup"><span data-stu-id="fde0a-105">Number of messages that are rejected by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="fde0a-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="fde0a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fde0a-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="fde0a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
