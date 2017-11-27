---
title: "Thread.Suspend Çöp Toplama ve Güvenli Noktalar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e47674ef8d1b1a7487e42765bcbce4b33cf98769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="966b2-102">Thread.Suspend Çöp Toplama ve Güvenli Noktalar</span><span class="sxs-lookup"><span data-stu-id="966b2-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="966b2-103">Çağırdığınızda <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> bir iş parçacığında, bir iş parçacığı askıya istendi ve güvenli bir noktası iş parçacığı gerçekten askıya almadan önce ulaştı kadar yürütmek iş parçacığı verir sistem notlar.</span><span class="sxs-lookup"><span data-stu-id="966b2-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="966b2-104">Bir güvenli iş parçacığı yürütmesi sırasında hangi atık toplama gerçekleştirilebilir noktasında noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="966b2-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="966b2-105">Çalışma zamanı güvenli bir noktaya ulaşıldığında, askıya alınmış iş parçacığı yönetilen kodda herhangi gelişme yapmaz güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="966b2-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="966b2-106">Her zaman dışında yönetilen kod parçacığı atık toplama için güvenli ve yönetilen kodun yürütülmesini sürdürmek deneme kadar yürütülmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="966b2-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="966b2-107">Çöp toplama gerçekleştirmek için çalışma zamanı koleksiyonu gerçekleştiren iş parçacığı dışında tüm iş parçacıklarını askıya alma gerekir.</span><span class="sxs-lookup"><span data-stu-id="966b2-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="966b2-108">Askıya alınmadan önce her bir iş parçacığı güvenli noktasına duruma getirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="966b2-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="966b2-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="966b2-109">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [<span data-ttu-id="966b2-110">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="966b2-110">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="966b2-111">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="966b2-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)
