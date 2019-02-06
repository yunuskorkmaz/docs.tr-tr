---
title: İş parçacığı nesneleri ve özellikleri
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f25609bc3c4dd829c66a1a4514b7f1121f9c0909
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759034"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="f773d-102">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="f773d-102">Threading objects and features</span></span>

<span data-ttu-id="f773d-103">İle birlikte <xref:System.Threading.Thread?displayProperty=nameWithType> .NET sağlar sınıfını yardımcı sınıfları sayısı çok iş parçacıklı uygulamalar geliştirin.</span><span class="sxs-lookup"><span data-stu-id="f773d-103">Along with the <xref:System.Threading.Thread?displayProperty=nameWithType> class, .NET provides a number of classes that help you develop multithreaded applications.</span></span> <span data-ttu-id="f773d-104">Aşağıdaki makaleler bu sınıflara genel bakış sunar:</span><span class="sxs-lookup"><span data-stu-id="f773d-104">The following articles provide overview of those classes:</span></span>

|<span data-ttu-id="f773d-105">Başlık</span><span class="sxs-lookup"><span data-stu-id="f773d-105">Title</span></span>|<span data-ttu-id="f773d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f773d-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f773d-107">Yönetilen iş parçacığı havuzu</span><span class="sxs-lookup"><span data-stu-id="f773d-107">The managed thread pool</span></span>](the-managed-thread-pool.md)|<span data-ttu-id="f773d-108">Açıklar <xref:System.Threading.ThreadPool?displayProperty=nameWithType> .NET tarafından yönetilen çalışan iş parçacığı havuzu sağlar sınıfını.</span><span class="sxs-lookup"><span data-stu-id="f773d-108">Describes the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> class, which provides a pool of worker threads that are managed by .NET.</span></span>|  
|[<span data-ttu-id="f773d-109">Süreölçerler</span><span class="sxs-lookup"><span data-stu-id="f773d-109">Timers</span></span>](timers.md)|<span data-ttu-id="f773d-110">Çok iş parçacıklı bir ortamda kullanılabilir .NET zamanlayıcılar açıklar.</span><span class="sxs-lookup"><span data-stu-id="f773d-110">Describes .NET timers that can be used in a multithreaded environment.</span></span>|
|[<span data-ttu-id="f773d-111">Eşitleme temellerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="f773d-111">Overview of synchronization primitives</span></span>](overview-of-synchronization-primitives.md)|<span data-ttu-id="f773d-112">Bir paylaşılan kaynağa veya denetimi iş parçacığı etkileşim erişimi eşitlemek için kullanılan türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f773d-112">Describes types that can be used to synchronize access to a shared resource or control thread interaction.</span></span>|
|[<span data-ttu-id="f773d-113">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="f773d-113">EventWaitHandle</span></span>](eventwaithandle.md)|<span data-ttu-id="f773d-114">Açıklar <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> iş parçacığı eşitleme olayını temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="f773d-114">Describes the <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> class, which represents a thread synchronization event.</span></span>|
|[<span data-ttu-id="f773d-115">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="f773d-115">CountdownEvent</span></span>](countdownevent.md)|<span data-ttu-id="f773d-116">Açıklar <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> kendi sayısı sıfır olduğunda, ayarladığınız duruma bir iş parçacığı eşitleme olay temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="f773d-116">Describes the <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> class, which represents a thread synchronization event that becomes set when its count is zero.</span></span>|
|[<span data-ttu-id="f773d-117">Karşılıklı dışlamalar</span><span class="sxs-lookup"><span data-stu-id="f773d-117">Mutexes</span></span>](mutexes.md)|<span data-ttu-id="f773d-118">Açıklar <xref:System.Threading.Mutex?displayProperty=nameWithType> , paylaşılan bir kaynağa özel erişim veren sınıf.</span><span class="sxs-lookup"><span data-stu-id="f773d-118">Describes the <xref:System.Threading.Mutex?displayProperty=nameWithType> class, which grants exclusive access to a shared resource.</span></span>|
|[<span data-ttu-id="f773d-119">Semaphore ve SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="f773d-119">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)|<span data-ttu-id="f773d-120">Açıklar <xref:System.Threading.Semaphore?displayProperty=nameWithType> sınıfını, paylaşılan bir kaynağa erişmek için iş parçacığı sayısı veya bir kaynak havuzu eşzamanlı olarak sınırlar.</span><span class="sxs-lookup"><span data-stu-id="f773d-120">Describes the <xref:System.Threading.Semaphore?displayProperty=nameWithType> class, which limits number of threads that can access a shared resource or a pool of resources concurrently.</span></span>|
|[<span data-ttu-id="f773d-121">Engel</span><span class="sxs-lookup"><span data-stu-id="f773d-121">Barrier</span></span>](barrier.md)|<span data-ttu-id="f773d-122">Açıklar <xref:System.Threading.Barrier?displayProperty=nameWithType> sınıfını aşamalı işlemlerinde koordinasyon iş parçacıklarının engeli desenini uygular.</span><span class="sxs-lookup"><span data-stu-id="f773d-122">Describes the <xref:System.Threading.Barrier?displayProperty=nameWithType> class, which implements the barrier pattern for coordination of threads in phased operations.</span></span>|
|[<span data-ttu-id="f773d-123">SpinLock</span><span class="sxs-lookup"><span data-stu-id="f773d-123">SpinLock</span></span>](spinlock.md)|<span data-ttu-id="f773d-124">Açıklar <xref:System.Threading.SpinLock?displayProperty=nameWithType> hafif bir yapısı için alternatif <xref:System.Threading.Monitor?displayProperty=nameWithType> belirli alt düzey kilitleme senaryoları için sınıf.</span><span class="sxs-lookup"><span data-stu-id="f773d-124">Describes the <xref:System.Threading.SpinLock?displayProperty=nameWithType> structure, which is a lightweight alternative to the <xref:System.Threading.Monitor?displayProperty=nameWithType> class for certain low-level locking scenarios.</span></span>|
|[<span data-ttu-id="f773d-125">SpinWait</span><span class="sxs-lookup"><span data-stu-id="f773d-125">SpinWait</span></span>](spinwait.md)|<span data-ttu-id="f773d-126">Açıklar <xref:System.Threading.SpinWait?displayProperty=nameWithType> yapısı, döndürme tabanlı bekleme için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f773d-126">Describes the <xref:System.Threading.SpinWait?displayProperty=nameWithType> structure, which provides support for spin-based waiting.</span></span>|

## <a name="see-also"></a><span data-ttu-id="f773d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f773d-127">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [<span data-ttu-id="f773d-128">İş parçacığı kullanma ve iş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="f773d-128">Using threads and threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="f773d-129">Zaman Uyumsuz Dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="f773d-129">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)
- [<span data-ttu-id="f773d-130">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="f773d-130">Parallel Programming</span></span>](../parallel-programming/index.md)
- [<span data-ttu-id="f773d-131">Görev Paralel Kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="f773d-131">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)
