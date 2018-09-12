---
title: Thread.Suspend Çöp Toplama ve Güvenli Noktalar
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc3af01167fe97b701bdb0c7bc37af02d8e8a77c
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44511912"
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="bc982-102">Thread.Suspend Çöp Toplama ve Güvenli Noktalar</span><span class="sxs-lookup"><span data-stu-id="bc982-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="bc982-103">Çağırdığınızda <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> bir iş parçacığında, bir iş parçacığını askıya alma isteğinde bulundu ve güvenli bir noktadan aslında bir iş parçacığını askıya almadan önce ulaştı kadar yürütmek iş parçacığının sağlar sistem notlar.</span><span class="sxs-lookup"><span data-stu-id="bc982-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="bc982-104">Bir güvenli iş parçacığı hangi çöp toplama gerçekleştirilebilir, yürütme noktasında noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="bc982-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="bc982-105">Güvenli bir noktasına ulaşıldığında, çalışma zamanı askıya alınan iş parçacığı yönetilen kodda herhangi bir gelişme yapmaz garanti eder.</span><span class="sxs-lookup"><span data-stu-id="bc982-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="bc982-106">Her zaman dışında yönetilen bir kodu yürüten bir iş parçacığı çöp toplama işlemi için güvenli ve yönetilen kodun yürütülmesini sürdürmek deneme kadar yürütülmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="bc982-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc982-107">Bir atık toplama işlemi gerçekleştirmek için çalışma zamanı dışında koleksiyonu gerçekleştiren iş parçacığının tüm iş parçacıkları askıya gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc982-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="bc982-108">Askıya alınmadan önce her bir iş parçacığı güvenli bir noktaya sunulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc982-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc982-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc982-109">See also</span></span>

- <xref:System.Threading.Thread>  
- <xref:System.GC>  
- [<span data-ttu-id="bc982-110">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="bc982-110">Threading</span></span>](../../../docs/standard/threading/index.md)  
- [<span data-ttu-id="bc982-111">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="bc982-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)
