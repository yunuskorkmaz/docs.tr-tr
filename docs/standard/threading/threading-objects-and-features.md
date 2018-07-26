---
title: İş Parçacığı Nesneleri ve Özellikleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d689aeb91ad79b776c3b93c1809ec46947ea60b
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874793"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="4b671-102">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="4b671-102">Threading Objects and Features</span></span>
<span data-ttu-id="4b671-103">.NET Framework yardımcı nesnelerin sayısını sağlar. birden çok iş parçacıklı uygulamaları oluşturmak ve yönetmek.</span><span class="sxs-lookup"><span data-stu-id="4b671-103">The .NET Framework provides a number of objects that help you create and manage multithreaded applications.</span></span> <span data-ttu-id="4b671-104">Yönetilen iş parçacıkları tarafından temsil edilir <xref:System.Threading.Thread> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4b671-104">Managed threads are represented by the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="4b671-105"><xref:System.Threading.ThreadPool> Kolay oluşturulması ve yönetimi, çok iş parçacıklı arka plan görevlerinin sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b671-105">The <xref:System.Threading.ThreadPool> class provides easy creation and management of multithreaded background tasks.</span></span> <span data-ttu-id="4b671-106"><xref:System.ComponentModel.BackgroundWorker> Sınıfla aynı kullanıcı arabirimi ile etkileşim görevler için.</span><span class="sxs-lookup"><span data-stu-id="4b671-106">The <xref:System.ComponentModel.BackgroundWorker> class does the same for tasks that interact with the user interface.</span></span> <span data-ttu-id="4b671-107"><xref:System.Threading.Timer> Sınıfı zaman aralıklarında arka plan görevleri yürütür.</span><span class="sxs-lookup"><span data-stu-id="4b671-107">The <xref:System.Threading.Timer> class executes background tasks at timed intervals.</span></span>  
  
 <span data-ttu-id="4b671-108">Ayrıca, bir dizi etkinlikler dahil olmak üzere iş parçacığı, eşitleme sınıfları vardır <xref:System.Threading.Semaphore> ve <xref:System.Threading.EventWaitHandle> .NET Framework 2.0 sürümünde sunulan sınıfları.</span><span class="sxs-lookup"><span data-stu-id="4b671-108">In addition, there are a number of classes that synchronize activities of threads, including the <xref:System.Threading.Semaphore> and <xref:System.Threading.EventWaitHandle> classes introduced in the .NET Framework version 2.0.</span></span> <span data-ttu-id="4b671-109">İçinde bu sınıflarının özellikleri karşılaştırılır [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="4b671-109">The features of these classes are compared in [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b671-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4b671-110">In This Section</span></span>  
 [<span data-ttu-id="4b671-111">Yönetilen İş Parçacığı Havuzu</span><span class="sxs-lookup"><span data-stu-id="4b671-111">The Managed Thread Pool</span></span>](../../../docs/standard/threading/the-managed-thread-pool.md)  
 <span data-ttu-id="4b671-112">Açıklar **iş parçacığı havuzu** herhangi bir iş parçacığı yönetim kendiniz yapmak zorunda kalmadan bir görev yürütmek için bir iş parçacığı istemenizi sağlar sınıfını.</span><span class="sxs-lookup"><span data-stu-id="4b671-112">Explains the **ThreadPool** class, which enables you to request a thread to execute a task without having to do any thread management yourself.</span></span>  
  
 [<span data-ttu-id="4b671-113">Süreölçerler</span><span class="sxs-lookup"><span data-stu-id="4b671-113">Timers</span></span>](../../../docs/standard/threading/timers.md)  
 <span data-ttu-id="4b671-114">Çok iş parçacıklı bir ortamda kullanılabilir zamanlayıcılar açıklar.</span><span class="sxs-lookup"><span data-stu-id="4b671-114">Describes timers that can be used in a multithreaded environment.</span></span>  
  
 [<span data-ttu-id="4b671-115">İzleyiciler</span><span class="sxs-lookup"><span data-stu-id="4b671-115">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 <span data-ttu-id="4b671-116">Nasıl kullanılacağını açıklar **İzleyici** sınıf üyesi erişimi eşitlemek için veya kendi iş parçacığı yönetimi türleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="4b671-116">Explains how to use the **Monitor** class to synchronize access to a member or to build your own thread management types.</span></span>  
  
 [<span data-ttu-id="4b671-117">Bekleme tanıtıcıları</span><span class="sxs-lookup"><span data-stu-id="4b671-117">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="4b671-118">Açıklar <xref:System.Threading.WaitHandle> sınıfı, olay yönelik soyut temel sınıf bekleme tanıtıcıları, mutex'leri ve birden çok eşitleme olay beklemek sağlayan semaforları.</span><span class="sxs-lookup"><span data-stu-id="4b671-118">Describes the <xref:System.Threading.WaitHandle> class, the abstract base class for event wait handles, mutexes, and semaphores, which enables waiting for multiple synchronization events.</span></span>  
  
 [<span data-ttu-id="4b671-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="4b671-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 <span data-ttu-id="4b671-120">Sinyal ve sinyalleri için bekleyen iş parçacığı etkinlikleri eşitlemek için kullanılan yönetilen bir olay bekleme tanıtıcıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="4b671-120">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>  
  
 [<span data-ttu-id="4b671-121">Karşılıklı dışlamalar</span><span class="sxs-lookup"><span data-stu-id="4b671-121">Mutexes</span></span>](../../../docs/standard/threading/mutexes.md)  
 <span data-ttu-id="4b671-122">Nasıl kullanılacağını açıklayan bir <xref:System.Threading.Mutex> bir nesneye erişimi eşitleme ya da kendi eşitleme mekanizmaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4b671-122">Explains how to use a <xref:System.Threading.Mutex> to synchronize access to an object or to build your own synchronization mechanisms.</span></span>  
  
 [<span data-ttu-id="4b671-123">Birbirine Kenetlenmiş İşlemler</span><span class="sxs-lookup"><span data-stu-id="4b671-123">Interlocked Operations</span></span>](../../../docs/standard/threading/interlocked-operations.md)  
 <span data-ttu-id="4b671-124">Nasıl kullanılacağını açıklar <xref:System.Threading.Interlocked> artırın veya bir değer azaltma ve tek bir atomik işlemde değeri depolamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="4b671-124">Explains how to use the <xref:System.Threading.Interlocked> class to increment or decrement a value and store the value in a single atomic operation.</span></span>  
  
 [<span data-ttu-id="4b671-125">Okuyucu-Yazıcı Kilitleri</span><span class="sxs-lookup"><span data-stu-id="4b671-125">Reader-Writer Locks</span></span>](../../../docs/standard/threading/reader-writer-locks.md)  
 <span data-ttu-id="4b671-126">Tek yazıcı/birden çok okuyucu semantiği uygulayan bir kilit tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4b671-126">Defines a lock that implements single-writer/multiple-reader semantics.</span></span>  
  
 [<span data-ttu-id="4b671-127">Semaphore ve SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="4b671-127">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 <span data-ttu-id="4b671-128">Açıklar <xref:System.Threading.Semaphore> nesneleri ve bunları sınırlı kaynaklara erişimi denetlemek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4b671-128">Describes <xref:System.Threading.Semaphore> objects and explains how to use them to control access to limited resources.</span></span>  
  
 [<span data-ttu-id="4b671-129">Eşitleme Temellerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4b671-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="4b671-130">.NET Framework sınıfları kilitleme ve yönetilen iş parçacıklarını eşitleme için sağlanan özellikler karşılaştırılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4b671-130">Compares the features of the .NET Framework classes provided for locking and synchronizing managed threads.</span></span>  
  
 [<span data-ttu-id="4b671-131">Engel</span><span class="sxs-lookup"><span data-stu-id="4b671-131">Barrier</span></span>](../../../docs/standard/threading/barrier.md)  
 <span data-ttu-id="4b671-132">Açıklar <xref:System.Threading.Barrier> koordinasyon iş parçacıklarının engeli desenini aşamalı işlemlerinde uygulayan nesneler.</span><span class="sxs-lookup"><span data-stu-id="4b671-132">Describes <xref:System.Threading.Barrier> objects that implement the barrier pattern for coordination of threads in phased operations.</span></span>  
  
 [<span data-ttu-id="4b671-133">SpinLock</span><span class="sxs-lookup"><span data-stu-id="4b671-133">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)  
 <span data-ttu-id="4b671-134">Açıklar <xref:System.Threading.SpinLock>, hafif bir izleme sınıfı belirli bir alt düzey senaryoları için alternatif.</span><span class="sxs-lookup"><span data-stu-id="4b671-134">Describes <xref:System.Threading.SpinLock>, a lightweight alternative to the Monitor class for certain low-level scenarios.</span></span>  
  
 [<span data-ttu-id="4b671-135">SpinWait</span><span class="sxs-lookup"><span data-stu-id="4b671-135">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 <span data-ttu-id="4b671-136">Açıklar <xref:System.Threading.SpinWait>, düşük düzeyli eşitleme temel nesne çekirdek tabanlı bekleme başlatmadan önce meşgul dönme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="4b671-136">Describes <xref:System.Threading.SpinWait>, a low level synchronization primitive that performs busy spinning prior to initiating a kernel-based wait.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4b671-137">Başvuru</span><span class="sxs-lookup"><span data-stu-id="4b671-137">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="4b671-138">İçin başvuru belgeleri sağlar **iş parçacığı** yönetilmeyen koddan gelen veya yönetilen bir uygulamada oluşturulan yönetilen iş parçacığı temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="4b671-138">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="4b671-139">Arka plan görevleri, kullanıcı arabirimi iş parçacığında harekete geçirilen olayları aracılığıyla iletişim kuran kullanıcı arabirimi ile etkileşim sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b671-139">Enables background tasks that interact with the user interface, communicating via events raised on the user-interface thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4b671-140">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="4b671-140">Related Sections</span></span>  
 [<span data-ttu-id="4b671-141">Zaman Uyumsuz Dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="4b671-141">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="4b671-142">Nasıl g/ç zaman uyumsuz tamamlama bağlantı noktalarını yalnızca bir giriş/çıkış işlemi tamamlandığında işleme gerektirecek şekilde iş parçacığı havuzu kullanma açıklar.</span><span class="sxs-lookup"><span data-stu-id="4b671-142">Describes how I/O asynchronous completion ports use the thread pool to require processing only when an input/output operation completes.</span></span>  
  
 [<span data-ttu-id="4b671-143">Görev Paralel Kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="4b671-143">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="4b671-144">Çok iş parçacıklı programlama için önerilen yaklaşım açıklar [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ve daha sonra.</span><span class="sxs-lookup"><span data-stu-id="4b671-144">Describes the recommended approach for multithreaded programming in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and later.</span></span>
