---
title: "İş Parçacığı Nesneleri ve Özellikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a73e5c60a661c171e9e46e6307484cf5e0e6b80
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="9d6be-102">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="9d6be-102">Threading Objects and Features</span></span>
<span data-ttu-id="9d6be-103">.NET Framework yardımcı nesne sayısı sağlar birden çok iş parçacıklı uygulamaları oluşturmak ve yönetmek.</span><span class="sxs-lookup"><span data-stu-id="9d6be-103">The .NET Framework provides a number of objects that help you create and manage multithreaded applications.</span></span> <span data-ttu-id="9d6be-104">Yönetilen iş parçacığı tarafından gösterilen <xref:System.Threading.Thread> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9d6be-104">Managed threads are represented by the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="9d6be-105"><xref:System.Threading.ThreadPool> Sınıfı, kolay oluşturulmasını ve birden çok iş parçacıklı arka plan görevleri yönetimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d6be-105">The <xref:System.Threading.ThreadPool> class provides easy creation and management of multithreaded background tasks.</span></span> <span data-ttu-id="9d6be-106"><xref:System.ComponentModel.BackgroundWorker> Sınıfı kullanıcı arabirimiyle etkileşim görevler için aynı değil.</span><span class="sxs-lookup"><span data-stu-id="9d6be-106">The <xref:System.ComponentModel.BackgroundWorker> class does the same for tasks that interact with the user interface.</span></span> <span data-ttu-id="9d6be-107"><xref:System.Threading.Timer> Sınıfı zaman aralıklarında arka plan görevleri yürütür.</span><span class="sxs-lookup"><span data-stu-id="9d6be-107">The <xref:System.Threading.Timer> class executes background tasks at timed intervals.</span></span>  
  
 <span data-ttu-id="9d6be-108">Ayrıca, bir dizi etkinlikler dahil olmak üzere iş parçacığı eşitleme sınıfları vardır <xref:System.Threading.Semaphore> ve <xref:System.Threading.EventWaitHandle> .NET Framework 2.0 sürümünde sunulan sınıfları.</span><span class="sxs-lookup"><span data-stu-id="9d6be-108">In addition, there are a number of classes that synchronize activities of threads, including the <xref:System.Threading.Semaphore> and <xref:System.Threading.EventWaitHandle> classes introduced in the .NET Framework version 2.0.</span></span> <span data-ttu-id="9d6be-109">Bu sınıfların özelliklerini de karşılaştırılır [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="9d6be-109">The features of these classes are compared in [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d6be-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9d6be-110">In This Section</span></span>  
 [<span data-ttu-id="9d6be-111">Yönetilen iş parçacığı havuzu</span><span class="sxs-lookup"><span data-stu-id="9d6be-111">The Managed Thread Pool</span></span>](../../../docs/standard/threading/the-managed-thread-pool.md)  
 <span data-ttu-id="9d6be-112">Açıklar **Threadpool'u** herhangi bir iş parçacığı yönetim kendiniz yapmak zorunda kalmadan bir görevi çalıştırmak için bir iş parçacığı isteği sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="9d6be-112">Explains the **ThreadPool** class, which enables you to request a thread to execute a task without having to do any thread management yourself.</span></span>  
  
 [<span data-ttu-id="9d6be-113">Zamanlayıcılar</span><span class="sxs-lookup"><span data-stu-id="9d6be-113">Timers</span></span>](../../../docs/standard/threading/timers.md)  
 <span data-ttu-id="9d6be-114">Nasıl kullanılacağı açıklanmaktadır bir **Zamanlayıcı** belirli bir zamanda çağrılan bir temsilciyi belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="9d6be-114">Explains how to use a **Timer** to specify a delegate to be called at a specified time.</span></span>  
  
 [<span data-ttu-id="9d6be-115">İzleyicileri</span><span class="sxs-lookup"><span data-stu-id="9d6be-115">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 <span data-ttu-id="9d6be-116">Nasıl kullanılacağı açıklanmaktadır **İzleyici** sınıf üyesi erişimi eşitlemek için ya da kendi iş parçacığı yönetim türleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9d6be-116">Explains how to use the **Monitor** class to synchronize access to a member or to build your own thread management types.</span></span>  
  
 [<span data-ttu-id="9d6be-117">Bekleme tanıtıcıları</span><span class="sxs-lookup"><span data-stu-id="9d6be-117">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="9d6be-118">Açıklar <xref:System.Threading.WaitHandle> sınıfı, olay için Özet temel sınıf bekleme tanıtıcıları, zaman uyumu sağlayıcılar ve birden çok eşitleme olay bekleniyor etkinleştirir semafor.</span><span class="sxs-lookup"><span data-stu-id="9d6be-118">Describes the <xref:System.Threading.WaitHandle> class, the abstract base class for event wait handles, mutexes, and semaphores, which enables waiting for multiple synchronization events.</span></span>  
  
 [<span data-ttu-id="9d6be-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="9d6be-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 <span data-ttu-id="9d6be-120">Sinyal ve sinyalleri için bekleyen iş parçacığı etkinliklerini eşitlemek için kullanılan yönetilen olay bekleme tanıtıcıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="9d6be-120">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>  
  
 [<span data-ttu-id="9d6be-121">Zaman uyumu sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="9d6be-121">Mutexes</span></span>](../../../docs/standard/threading/mutexes.md)  
 <span data-ttu-id="9d6be-122">Nasıl kullanılacağı açıklanmaktadır bir <xref:System.Threading.Mutex> bir nesneye erişimi eşitlemek ya da kendi eşitleme mekanizmaları oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9d6be-122">Explains how to use a <xref:System.Threading.Mutex> to synchronize access to an object or to build your own synchronization mechanisms.</span></span>  
  
 [<span data-ttu-id="9d6be-123">Birbirine kenetlenmiş işlemler</span><span class="sxs-lookup"><span data-stu-id="9d6be-123">Interlocked Operations</span></span>](../../../docs/standard/threading/interlocked-operations.md)  
 <span data-ttu-id="9d6be-124">Nasıl kullanılacağı açıklanmaktadır <xref:System.Threading.Interlocked> artırın veya bir değer azaltma ve tek bir atomik işlemle değeri depolamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="9d6be-124">Explains how to use the <xref:System.Threading.Interlocked> class to increment or decrement a value and store the value in a single atomic operation.</span></span>  
  
 [<span data-ttu-id="9d6be-125">Okuyucu-Yazıcı kilitleri</span><span class="sxs-lookup"><span data-stu-id="9d6be-125">Reader-Writer Locks</span></span>](../../../docs/standard/threading/reader-writer-locks.md)  
 <span data-ttu-id="9d6be-126">Tek yazıcı/birden çok okuyucu semantiğini uygular bir kilit tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9d6be-126">Defines a lock that implements single-writer/multiple-reader semantics.</span></span>  
  
 [<span data-ttu-id="9d6be-127">Semafor ve SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="9d6be-127">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 <span data-ttu-id="9d6be-128">Açıklar <xref:System.Threading.Semaphore> nesnelerini ve bunların sınırlı kaynaklara erişimi denetlemek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9d6be-128">Describes <xref:System.Threading.Semaphore> objects and explains how to use them to control access to limited resources.</span></span>  
  
 [<span data-ttu-id="9d6be-129">Eşitleme temellerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="9d6be-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="9d6be-130">Kilitleme ve yönetilen iş parçacıklarını eşitleme için sağlanan .NET Framework sınıfları özellikleri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="9d6be-130">Compares the features of the .NET Framework classes provided for locking and synchronizing managed threads.</span></span>  
  
 [<span data-ttu-id="9d6be-131">Engelle</span><span class="sxs-lookup"><span data-stu-id="9d6be-131">Barrier</span></span>](../../../docs/standard/threading/barrier.md)  
 <span data-ttu-id="9d6be-132">Açıklar <xref:System.Threading.Barrier> aşamalı işlemlerinde düzenleme iş parçacığı engel desenini uygulayan nesneler.</span><span class="sxs-lookup"><span data-stu-id="9d6be-132">Describes <xref:System.Threading.Barrier> objects that implement the barrier pattern for coordination of threads in phased operations.</span></span>  
  
 [<span data-ttu-id="9d6be-133">SpinLock</span><span class="sxs-lookup"><span data-stu-id="9d6be-133">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)  
 <span data-ttu-id="9d6be-134">Açıklar <xref:System.Threading.SpinLock>, alt düzey belirli senaryolar için izleme sınıfı için basit bir alternatif.</span><span class="sxs-lookup"><span data-stu-id="9d6be-134">Describes <xref:System.Threading.SpinLock>, a lightweight alternative to the Monitor class for certain low-level scenarios.</span></span>  
  
 [<span data-ttu-id="9d6be-135">SpinWait</span><span class="sxs-lookup"><span data-stu-id="9d6be-135">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 <span data-ttu-id="9d6be-136">Açıklar <xref:System.Threading.SpinWait>, düşük düzeyli eşitleme ilkel çekirdek tabanlı bekleme başlatmadan önce meşgul dönen gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="9d6be-136">Describes <xref:System.Threading.SpinWait>, a low level synchronization primitive that performs busy spinning prior to initiating a kernel-based wait.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9d6be-137">Başvuru</span><span class="sxs-lookup"><span data-stu-id="9d6be-137">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="9d6be-138">Başvuru belgelerine sağlar **iş parçacığı** yönetilmeyen koddan gelen veya yönetilen bir uygulamada oluşturuldu, yönetilen bir iş parçacığı temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="9d6be-138">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="9d6be-139">Kullanıcı arabirimi iş parçacığı üzerinde oluşturulan olaylara aracılığıyla iletişim kurmasını kullanıcı arabirimiyle etkileşim arka plan görevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d6be-139">Enables background tasks that interact with the user interface, communicating via events raised on the user-interface thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9d6be-140">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9d6be-140">Related Sections</span></span>  
 [<span data-ttu-id="9d6be-141">Zaman uyumsuz dosya g/ç</span><span class="sxs-lookup"><span data-stu-id="9d6be-141">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="9d6be-142">İş parçacığı havuzu g/ç zaman uyumsuz tamamlama bağlantı noktalarını yalnızca bir giriş/çıkış işlem tamamlandığında işleme gerektiren için nasıl kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9d6be-142">Describes how I/O asynchronous completion ports use the thread pool to require processing only when an input/output operation completes.</span></span>  
  
 [<span data-ttu-id="9d6be-143">Görev paralel kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="9d6be-143">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="9d6be-144">Birden çok iş parçacıklı programlama için önerilen yaklaşım açıklar [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ve daha sonra.</span><span class="sxs-lookup"><span data-stu-id="9d6be-144">Describes the recommended approach for multithreaded programming in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and later.</span></span>
