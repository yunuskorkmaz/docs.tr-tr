---
title: İş parçacığı nesneleri ve özellikleri
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
ms.openlocfilehash: dd9b7b8cb194353d0a1c285af10d54dc7366896e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128967"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="87aff-102">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="87aff-102">Threading objects and features</span></span>

<span data-ttu-id="87aff-103"><xref:System.Threading.Thread?displayProperty=nameWithType> .NET, sınıfla birlikte çok iş parçacığı uygulamaları geliştirmenize yardımcı olan bir dizi sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="87aff-103">Along with the <xref:System.Threading.Thread?displayProperty=nameWithType> class, .NET provides a number of classes that help you develop multithreaded applications.</span></span> <span data-ttu-id="87aff-104">Aşağıdaki makaleler bu sınıflara genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="87aff-104">The following articles provide overview of those classes:</span></span>

|<span data-ttu-id="87aff-105">Başlık</span><span class="sxs-lookup"><span data-stu-id="87aff-105">Title</span></span>|<span data-ttu-id="87aff-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87aff-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="87aff-107">Yönetilen iş parçacığı havuzu</span><span class="sxs-lookup"><span data-stu-id="87aff-107">The managed thread pool</span></span>](the-managed-thread-pool.md)|<span data-ttu-id="87aff-108">.NET <xref:System.Threading.ThreadPool?displayProperty=nameWithType> tarafından yönetilen bir alt iş parçacığı havuzu sağlayan sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="87aff-108">Describes the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> class, which provides a pool of worker threads that are managed by .NET.</span></span>|  
|[<span data-ttu-id="87aff-109">Zamanlayıcılar</span><span class="sxs-lookup"><span data-stu-id="87aff-109">Timers</span></span>](timers.md)|<span data-ttu-id="87aff-110">Çok iş parçacığı ortamında kullanılabilen .NET zamanlayıcılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="87aff-110">Describes .NET timers that can be used in a multithreaded environment.</span></span>|
|[<span data-ttu-id="87aff-111">Eşitleme temellerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="87aff-111">Overview of synchronization primitives</span></span>](overview-of-synchronization-primitives.md)|<span data-ttu-id="87aff-112">Paylaşılan bir kaynağa erişimi eşitlemek veya iş parçacığı etkileşimini denetlemek için kullanılabilecek türleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="87aff-112">Describes types that can be used to synchronize access to a shared resource or control thread interaction.</span></span>|
|[<span data-ttu-id="87aff-113">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="87aff-113">EventWaitHandle</span></span>](eventwaithandle.md)|<span data-ttu-id="87aff-114">İş <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> parçacığı eşitleme olayını temsil eden sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="87aff-114">Describes the <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> class, which represents a thread synchronization event.</span></span>|
|[<span data-ttu-id="87aff-115">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="87aff-115">CountdownEvent</span></span>](countdownevent.md)|<span data-ttu-id="87aff-116">Sayısı <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> sıfır olduğunda ayarlanan bir iş parçacığı eşitleme olayını temsil eden sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="87aff-116">Describes the <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> class, which represents a thread synchronization event that becomes set when its count is zero.</span></span>|
|[<span data-ttu-id="87aff-117">Karşılıklı dışlamalar</span><span class="sxs-lookup"><span data-stu-id="87aff-117">Mutexes</span></span>](mutexes.md)|<span data-ttu-id="87aff-118">Paylaşılan <xref:System.Threading.Mutex?displayProperty=nameWithType> kaynağa özel erişim sağlayan sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="87aff-118">Describes the <xref:System.Threading.Mutex?displayProperty=nameWithType> class, which grants exclusive access to a shared resource.</span></span>|
|[<span data-ttu-id="87aff-119">Semafor ve SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="87aff-119">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)|<span data-ttu-id="87aff-120">Paylaşılan <xref:System.Threading.Semaphore?displayProperty=nameWithType> bir kaynağa veya aynı anda bir kaynak havuzuna erişebilen iş parçacığı sayısını sınırlayan sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="87aff-120">Describes the <xref:System.Threading.Semaphore?displayProperty=nameWithType> class, which limits number of threads that can access a shared resource or a pool of resources concurrently.</span></span>|
|[<span data-ttu-id="87aff-121">Engel</span><span class="sxs-lookup"><span data-stu-id="87aff-121">Barrier</span></span>](barrier.md)|<span data-ttu-id="87aff-122">Aşamalı <xref:System.Threading.Barrier?displayProperty=nameWithType> işlemlerde iş parçacıklarının koordinasyonu için bariyer deseni uygulayan sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="87aff-122">Describes the <xref:System.Threading.Barrier?displayProperty=nameWithType> class, which implements the barrier pattern for coordination of threads in phased operations.</span></span>|
|[<span data-ttu-id="87aff-123">SpinLock</span><span class="sxs-lookup"><span data-stu-id="87aff-123">SpinLock</span></span>](spinlock.md)|<span data-ttu-id="87aff-124">Belirli <xref:System.Threading.SpinLock?displayProperty=nameWithType> düşük düzeyli kilitleme senaryoları <xref:System.Threading.Monitor?displayProperty=nameWithType> için sınıfa hafif bir alternatif olan yapıyı açıklar.</span><span class="sxs-lookup"><span data-stu-id="87aff-124">Describes the <xref:System.Threading.SpinLock?displayProperty=nameWithType> structure, which is a lightweight alternative to the <xref:System.Threading.Monitor?displayProperty=nameWithType> class for certain low-level locking scenarios.</span></span>|
|[<span data-ttu-id="87aff-125">SpinWait</span><span class="sxs-lookup"><span data-stu-id="87aff-125">SpinWait</span></span>](spinwait.md)|<span data-ttu-id="87aff-126">Spin <xref:System.Threading.SpinWait?displayProperty=nameWithType> tabanlı bekleme desteği sağlayan yapıyı açıklar.</span><span class="sxs-lookup"><span data-stu-id="87aff-126">Describes the <xref:System.Threading.SpinWait?displayProperty=nameWithType> structure, which provides support for spin-based waiting.</span></span>|

## <a name="see-also"></a><span data-ttu-id="87aff-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87aff-127">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [<span data-ttu-id="87aff-128">İş parçacıkları ve iş parçacığı oluşturmayı kullanma</span><span class="sxs-lookup"><span data-stu-id="87aff-128">Using threads and threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="87aff-129">Zaman Uyumsuz Dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="87aff-129">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)
- [<span data-ttu-id="87aff-130">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="87aff-130">Parallel Programming</span></span>](../parallel-programming/index.md)
- [<span data-ttu-id="87aff-131">Görev Paralel Kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="87aff-131">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)
