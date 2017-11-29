---
title: "Saniyede Kuyruğa Alınan Bırakılmış İleti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d7386b2f7c6d78dde41c88c66d216b99cc21050
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="617a3-102">Saniyede Kuyruğa Alınan Bırakılmış İleti</span><span class="sxs-lookup"><span data-stu-id="617a3-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="617a3-103">Sayaç adı: Saniye başına bırakılan iletileri kuyruğa alındı.</span><span class="sxs-lookup"><span data-stu-id="617a3-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="617a3-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="617a3-104">Description</span></span>  
 <span data-ttu-id="617a3-105">Sıraya alınan aktarım sırasında bu hizmet tarafından bir saniyede bırakılan ileti sayısı.</span><span class="sxs-lookup"><span data-stu-id="617a3-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="617a3-106">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="617a3-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="617a3-107">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="617a3-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
