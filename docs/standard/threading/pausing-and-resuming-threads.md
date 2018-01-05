---
title: "İş Parçacıklarını Duraklatma ve Sürdürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resuming threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4b87fbb51dbdcd5226a902e8b7ee5aeb7e126b7e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="pausing-and-resuming-threads"></a><span data-ttu-id="9c27f-102">İş Parçacıklarını Duraklatma ve Sürdürme</span><span class="sxs-lookup"><span data-stu-id="9c27f-102">Pausing and Resuming Threads</span></span>
<span data-ttu-id="9c27f-103">İş parçacığı etkinliklerini eşitlemek için en yaygın blok ve yayın iş parçacığı veya kilidi nesneleri veya kod bölümlerinin yollarıdır.</span><span class="sxs-lookup"><span data-stu-id="9c27f-103">The most common ways to synchronize the activities of threads are to block and release threads, or to lock objects or regions of code.</span></span> <span data-ttu-id="9c27f-104">Bu kilitleme ve mekanizmaları engelleme hakkında daha fazla bilgi için bkz: [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="9c27f-104">For more information on these locking and blocking mechanisms, see [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="9c27f-105">İş parçacığı kendilerini uyku moduna yerleştirmek de olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c27f-105">You can also have threads put themselves to sleep.</span></span> <span data-ttu-id="9c27f-106">Ne zaman iş parçacığı engellendi veya kullanabileceğiniz uyku, bir <xref:System.Threading.ThreadInterruptedException> bekleme durumlarını dışında ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="9c27f-106">When threads are blocked or sleeping, you can use a <xref:System.Threading.ThreadInterruptedException> to break them out of their wait states.</span></span>  
  
## <a name="the-threadsleep-method"></a><span data-ttu-id="9c27f-107">Thread.Sleep yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c27f-107">The Thread.Sleep Method</span></span>  
 <span data-ttu-id="9c27f-108">Çağırma <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> yöntemi milisaniye veya yöntemine geçirdiğiniz zaman aralığı sayısı hemen engellemek geçerli iş parçacığının neden olur ve başka bir iş parçacığı için kendi zaman dilimi kalanı verir.</span><span class="sxs-lookup"><span data-stu-id="9c27f-108">Calling the <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> method causes the current thread to immediately block for the number of milliseconds or the time interval you pass to the method, and yields the remainder of its time slice to another thread.</span></span> <span data-ttu-id="9c27f-109">Bu aralığı geçtikten sonra Uyuyan iş parçacığı yürütme devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="9c27f-109">Once that interval elapses, the sleeping thread resumes execution.</span></span>  
  
 <span data-ttu-id="9c27f-110">Bir iş parçacığı çağıramaz <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> başka bir iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="9c27f-110">One thread cannot call <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> on another thread.</span></span>  <span data-ttu-id="9c27f-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>her zaman uyku moduna geçerli iş parçacığının neden statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9c27f-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is a static method that always causes the current thread to sleep.</span></span>  
  
 <span data-ttu-id="9c27f-112">Çağırma <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> değerini <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> çağıran başka bir iş parçacığı tarafından kesilene kadar uyku için bir iş parçacığı neden <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> yöntemi Uyuyan iş parçacığı üzerinde veya bir çağrı tarafından durduruluncaya kadar kendi <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9c27f-112">Calling <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> with a value of <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> causes a thread to sleep until it is interrupted by another thread that calls the  <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the sleeping thread, or until it is terminated by a call to its <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="9c27f-113">Aşağıdaki örnek Uyuyan bir iş parçacığı kesintiye hem yöntemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9c27f-113">The following example illustrates both methods of interrupting a sleeping thread.</span></span>  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a><span data-ttu-id="9c27f-114">İş parçacığı kesintiye</span><span class="sxs-lookup"><span data-stu-id="9c27f-114">Interrupting Threads</span></span>  
 <span data-ttu-id="9c27f-115">Çağırarak bekleyen iş parçacığı kesintiye uğratabilir <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> yöntemi atmak için engellenmiş iş parçacığı üzerinde bir <xref:System.Threading.ThreadInterruptedException>, iş parçacığı engelleme çağrısı dışında keser.</span><span class="sxs-lookup"><span data-stu-id="9c27f-115">You can interrupt a waiting thread by calling the <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the blocked thread to throw a <xref:System.Threading.ThreadInterruptedException>, which breaks the thread out of the blocking call.</span></span> <span data-ttu-id="9c27f-116">İş parçacığı catch <xref:System.Threading.ThreadInterruptedException> ve ne olursa olsun çalışmaya devam etmek uygundur.</span><span class="sxs-lookup"><span data-stu-id="9c27f-116">The thread should catch the <xref:System.Threading.ThreadInterruptedException> and do whatever is appropriate to continue working.</span></span> <span data-ttu-id="9c27f-117">Özel iş parçacığı yoksayar, çalışma zamanı özel durumu yakalar ve iş parçacığı durdurur.</span><span class="sxs-lookup"><span data-stu-id="9c27f-117">If the thread ignores the exception, the runtime catches the exception and stops the thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c27f-118">Hedef iş parçacığı değilse ne zaman engellenen <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> olduğu olarak adlandırılan, iş parçacığı kadar blokları kesintiye uğramaz.</span><span class="sxs-lookup"><span data-stu-id="9c27f-118">If the target thread is not blocked when <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> is called, the thread is not interrupted until it blocks.</span></span> <span data-ttu-id="9c27f-119">İş parçacığı hiçbir zaman engelliyorsa hiç kesintiye olmadan işlemini tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="9c27f-119">If the thread never blocks, it could complete without ever being interrupted.</span></span>  
  
 <span data-ttu-id="9c27f-120">Bekleme yönetilen bekleyin, sonra ise <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> hem de iş parçacığı hemen Uyandırma.</span><span class="sxs-lookup"><span data-stu-id="9c27f-120">If a wait is a managed wait, then <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> both wake the thread immediately.</span></span> <span data-ttu-id="9c27f-121">Bekleme yönetilmeyen bekleme ise (örneğin, bir platform çağırma çağrısı Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) işlevi), hiçbiri <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ya da <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> döndürür veya yönetilen koda çağrı kadar iş parçacığı denetimini ele geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="9c27f-121">If a wait is an unmanaged wait (for example, a platform invoke call to the Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) function), neither <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nor <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> can take control of the thread until it returns to or calls into managed code.</span></span> <span data-ttu-id="9c27f-122">Yönetilen kodda davranış aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9c27f-122">In managed code, the behavior is as follows:</span></span>  
  
-   <span data-ttu-id="9c27f-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>bir iş parçacığı dışında olabilir ve neden olan tüm bekleme modundan bir <xref:System.Threading.ThreadInterruptedException> hedef iş parçacığında durum için.</span><span class="sxs-lookup"><span data-stu-id="9c27f-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadInterruptedException> to be thrown in the destination thread.</span></span>  
  
-   <span data-ttu-id="9c27f-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>bir iş parçacığı dışında olabilir ve neden olan tüm bekleme modundan bir <xref:System.Threading.ThreadAbortException> iş parçacığı üzerinde durum için.</span><span class="sxs-lookup"><span data-stu-id="9c27f-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadAbortException> to be thrown on the thread.</span></span> <span data-ttu-id="9c27f-125">Ayrıntılar için bkz [iş parçacıklarını yok etme](../../../docs/standard/threading/destroying-threads.md).</span><span class="sxs-lookup"><span data-stu-id="9c27f-125">For details, see [Destroying Threads](../../../docs/standard/threading/destroying-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c27f-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9c27f-126">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadInterruptedException>  
 <xref:System.Threading.ThreadAbortException>  
 [<span data-ttu-id="9c27f-127">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c27f-127">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="9c27f-128">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="9c27f-128">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 [<span data-ttu-id="9c27f-129">Eşitleme Temellerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9c27f-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
