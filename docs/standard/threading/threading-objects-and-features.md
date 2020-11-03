---
title: İş parçacığı nesneleri ve özellikleri
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
ms.openlocfilehash: 98fb9238b7cf9d11641628de1413e911985a87c3
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188152"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="7286a-102">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="7286a-102">Threading objects and features</span></span>

<span data-ttu-id="7286a-103"><xref:System.Threading.Thread?displayProperty=nameWithType>.NET sınıfı ile birlikte, çok iş parçacıklı uygulamalar geliştirmenize yardımcı olacak bir dizi sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="7286a-103">Along with the <xref:System.Threading.Thread?displayProperty=nameWithType> class, .NET provides a number of classes that help you develop multithreaded applications.</span></span> <span data-ttu-id="7286a-104">Aşağıdaki makaleler, bu sınıflara genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="7286a-104">The following articles provide overview of those classes:</span></span>

|<span data-ttu-id="7286a-105">Başlık</span><span class="sxs-lookup"><span data-stu-id="7286a-105">Title</span></span>|<span data-ttu-id="7286a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7286a-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7286a-107">Yönetilen iş parçacığı havuzu</span><span class="sxs-lookup"><span data-stu-id="7286a-107">The managed thread pool</span></span>](the-managed-thread-pool.md)|<span data-ttu-id="7286a-108"><xref:System.Threading.ThreadPool?displayProperty=nameWithType>.NET tarafından yönetilen bir çalışan iş parçacığı havuzu sağlayan sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7286a-108">Describes the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> class, which provides a pool of worker threads that are managed by .NET.</span></span>|  
|[<span data-ttu-id="7286a-109">Zamanlayıcılar</span><span class="sxs-lookup"><span data-stu-id="7286a-109">Timers</span></span>](timers.md)|<span data-ttu-id="7286a-110">Çoklu iş parçacıklı bir ortamda kullanılabilen .NET zamanlayıcıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7286a-110">Describes .NET timers that can be used in a multithreaded environment.</span></span>|
|[<span data-ttu-id="7286a-111">Eşitleme temellerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="7286a-111">Overview of synchronization primitives</span></span>](overview-of-synchronization-primitives.md)|<span data-ttu-id="7286a-112">Paylaşılan bir kaynağa veya denetim iş parçacığı etkileşimine erişimi eşzamanlı hale getirmek için kullanılabilecek türleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="7286a-112">Describes types that can be used to synchronize access to a shared resource or control thread interaction.</span></span>|
|[<span data-ttu-id="7286a-113">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="7286a-113">EventWaitHandle</span></span>](eventwaithandle.md)|<span data-ttu-id="7286a-114"><xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>İş parçacığı eşitleme olayını temsil eden sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7286a-114">Describes the <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> class, which represents a thread synchronization event.</span></span>|
|[<span data-ttu-id="7286a-115">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="7286a-115">CountdownEvent</span></span>](countdownevent.md)|<span data-ttu-id="7286a-116"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType>Sayısı sıfır olduğunda ayarlanmış bir iş parçacığı eşitleme olayını temsil eden sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7286a-116">Describes the <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> class, which represents a thread synchronization event that becomes set when its count is zero.</span></span>|
|[<span data-ttu-id="7286a-117">Zaman Uyumu Sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="7286a-117">Mutexes</span></span>](mutexes.md)|<span data-ttu-id="7286a-118"><xref:System.Threading.Mutex?displayProperty=nameWithType>Paylaşılan bir kaynağa özel erişim veren sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7286a-118">Describes the <xref:System.Threading.Mutex?displayProperty=nameWithType> class, which grants exclusive access to a shared resource.</span></span>|
|[<span data-ttu-id="7286a-119">Semafor ve SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="7286a-119">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)|<span data-ttu-id="7286a-120"><xref:System.Threading.Semaphore?displayProperty=nameWithType>Paylaşılan bir kaynağa veya bir kaynak havuzuna eşzamanlı olarak erişebilen iş parçacığı sayısını sınırlayan sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7286a-120">Describes the <xref:System.Threading.Semaphore?displayProperty=nameWithType> class, which limits number of threads that can access a shared resource or a pool of resources concurrently.</span></span>|
|[<span data-ttu-id="7286a-121">Engel</span><span class="sxs-lookup"><span data-stu-id="7286a-121">Barrier</span></span>](barrier.md)|<span data-ttu-id="7286a-122"><xref:System.Threading.Barrier?displayProperty=nameWithType>Aşamalı işlemlerde iş parçacıklarının koordinasyonu için engel modelini uygulayan sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7286a-122">Describes the <xref:System.Threading.Barrier?displayProperty=nameWithType> class, which implements the barrier pattern for coordination of threads in phased operations.</span></span>|
|[<span data-ttu-id="7286a-123">SpinLock</span><span class="sxs-lookup"><span data-stu-id="7286a-123">SpinLock</span></span>](spinlock.md)|<span data-ttu-id="7286a-124"><xref:System.Threading.SpinLock?displayProperty=nameWithType> <xref:System.Threading.Monitor?displayProperty=nameWithType> Belirli alt düzey kilitleme senaryolarında sınıfına hafif bir alternatif olan yapıyı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7286a-124">Describes the <xref:System.Threading.SpinLock?displayProperty=nameWithType> structure, which is a lightweight alternative to the <xref:System.Threading.Monitor?displayProperty=nameWithType> class for certain low-level locking scenarios.</span></span>|
|[<span data-ttu-id="7286a-125">SpinWait</span><span class="sxs-lookup"><span data-stu-id="7286a-125">SpinWait</span></span>](spinwait.md)|<span data-ttu-id="7286a-126"><xref:System.Threading.SpinWait?displayProperty=nameWithType>, Döndürme tabanlı bekleme desteği sağlayan yapıyı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7286a-126">Describes the <xref:System.Threading.SpinWait?displayProperty=nameWithType> structure, which provides support for spin-based waiting.</span></span>|

## <a name="see-also"></a><span data-ttu-id="7286a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7286a-127">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [<span data-ttu-id="7286a-128">İş parçacıkları ve iş parçacığı oluşturmayı kullanma</span><span class="sxs-lookup"><span data-stu-id="7286a-128">Using threads and threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="7286a-129">Zaman uyumsuz dosya g/ç</span><span class="sxs-lookup"><span data-stu-id="7286a-129">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)
- [<span data-ttu-id="7286a-130">Paralel programlama</span><span class="sxs-lookup"><span data-stu-id="7286a-130">Parallel Programming</span></span>](../parallel-programming/index.md)
- [<span data-ttu-id="7286a-131">Görev Paralel Kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="7286a-131">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)
