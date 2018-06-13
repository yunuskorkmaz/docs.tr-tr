---
title: Saniyede Kuyruğa Alınan Bırakılmış İleti
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: 47835086a4ee920e814d9dd6c1e41b9cdc33efec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471475"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="7db17-102">Saniyede Kuyruğa Alınan Bırakılmış İleti</span><span class="sxs-lookup"><span data-stu-id="7db17-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="7db17-103">Sayaç adı: Saniye başına bırakılan iletileri kuyruğa alındı.</span><span class="sxs-lookup"><span data-stu-id="7db17-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7db17-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7db17-104">Description</span></span>  
 <span data-ttu-id="7db17-105">Sıraya alınan aktarım sırasında bu hizmet tarafından bir saniyede bırakılan ileti sayısı.</span><span class="sxs-lookup"><span data-stu-id="7db17-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="7db17-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="7db17-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="7db17-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="7db17-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
