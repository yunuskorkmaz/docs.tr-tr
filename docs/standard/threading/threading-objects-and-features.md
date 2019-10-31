---
title: İş parçacığı nesneleri ve özellikleri
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
ms.openlocfilehash: dd9b7b8cb194353d0a1c285af10d54dc7366896e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128967"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="1649f-102">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="1649f-102">Threading objects and features</span></span>

<span data-ttu-id="1649f-103">.NET <xref:System.Threading.Thread?displayProperty=nameWithType> sınıfıyla birlikte çok iş parçacıklı uygulamalar geliştirmenize yardımcı olan bir dizi sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="1649f-103">Along with the <xref:System.Threading.Thread?displayProperty=nameWithType> class, .NET provides a number of classes that help you develop multithreaded applications.</span></span> <span data-ttu-id="1649f-104">Aşağıdaki makaleler, bu sınıflara genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="1649f-104">The following articles provide overview of those classes:</span></span>

|<span data-ttu-id="1649f-105">Başlık</span><span class="sxs-lookup"><span data-stu-id="1649f-105">Title</span></span>|<span data-ttu-id="1649f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1649f-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1649f-107">Yönetilen iş parçacığı havuzu</span><span class="sxs-lookup"><span data-stu-id="1649f-107">The managed thread pool</span></span>](the-managed-thread-pool.md)|<span data-ttu-id="1649f-108">.NET tarafından yönetilen bir çalışan iş parçacığı havuzu sağlayan <xref:System.Threading.ThreadPool?displayProperty=nameWithType> sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1649f-108">Describes the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> class, which provides a pool of worker threads that are managed by .NET.</span></span>|  
|[<span data-ttu-id="1649f-109">Süreölçerler</span><span class="sxs-lookup"><span data-stu-id="1649f-109">Timers</span></span>](timers.md)|<span data-ttu-id="1649f-110">Çoklu iş parçacıklı bir ortamda kullanılabilen .NET zamanlayıcıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1649f-110">Describes .NET timers that can be used in a multithreaded environment.</span></span>|
|[<span data-ttu-id="1649f-111">Eşitleme temelleri 'ne genel bakış</span><span class="sxs-lookup"><span data-stu-id="1649f-111">Overview of synchronization primitives</span></span>](overview-of-synchronization-primitives.md)|<span data-ttu-id="1649f-112">Paylaşılan bir kaynağa veya denetim iş parçacığı etkileşimine erişimi eşzamanlı hale getirmek için kullanılabilecek türleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="1649f-112">Describes types that can be used to synchronize access to a shared resource or control thread interaction.</span></span>|
|[<span data-ttu-id="1649f-113">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="1649f-113">EventWaitHandle</span></span>](eventwaithandle.md)|<span data-ttu-id="1649f-114">Bir iş parçacığı eşitleme olayını temsil eden <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1649f-114">Describes the <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> class, which represents a thread synchronization event.</span></span>|
|[<span data-ttu-id="1649f-115">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="1649f-115">CountdownEvent</span></span>](countdownevent.md)|<span data-ttu-id="1649f-116">Sayısı sıfır olduğunda ayarlanan bir iş parçacığı eşitleme olayını temsil eden <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1649f-116">Describes the <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> class, which represents a thread synchronization event that becomes set when its count is zero.</span></span>|
|[<span data-ttu-id="1649f-117">Karşılıklı dışlamalar</span><span class="sxs-lookup"><span data-stu-id="1649f-117">Mutexes</span></span>](mutexes.md)|<span data-ttu-id="1649f-118">Paylaşılan bir kaynağa özel erişim veren <xref:System.Threading.Mutex?displayProperty=nameWithType> sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1649f-118">Describes the <xref:System.Threading.Mutex?displayProperty=nameWithType> class, which grants exclusive access to a shared resource.</span></span>|
|[<span data-ttu-id="1649f-119">Semaphore ve SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="1649f-119">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)|<span data-ttu-id="1649f-120">Paylaşılan bir kaynağa veya bir kaynak havuzuna eşzamanlı olarak erişebilen iş parçacığı sayısını sınırlayan <xref:System.Threading.Semaphore?displayProperty=nameWithType> sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1649f-120">Describes the <xref:System.Threading.Semaphore?displayProperty=nameWithType> class, which limits number of threads that can access a shared resource or a pool of resources concurrently.</span></span>|
|[<span data-ttu-id="1649f-121">Engel</span><span class="sxs-lookup"><span data-stu-id="1649f-121">Barrier</span></span>](barrier.md)|<span data-ttu-id="1649f-122">Aşamalı işlemlerde iş parçacıklarının koordinasyonu için engel modelini uygulayan <xref:System.Threading.Barrier?displayProperty=nameWithType> sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1649f-122">Describes the <xref:System.Threading.Barrier?displayProperty=nameWithType> class, which implements the barrier pattern for coordination of threads in phased operations.</span></span>|
|[<span data-ttu-id="1649f-123">SpinLock</span><span class="sxs-lookup"><span data-stu-id="1649f-123">SpinLock</span></span>](spinlock.md)|<span data-ttu-id="1649f-124">Bazı düşük düzey kilitleme senaryoları için <xref:System.Threading.Monitor?displayProperty=nameWithType> sınıfına hafif bir alternatif olan <xref:System.Threading.SpinLock?displayProperty=nameWithType> yapısını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1649f-124">Describes the <xref:System.Threading.SpinLock?displayProperty=nameWithType> structure, which is a lightweight alternative to the <xref:System.Threading.Monitor?displayProperty=nameWithType> class for certain low-level locking scenarios.</span></span>|
|[<span data-ttu-id="1649f-125">SpinWait</span><span class="sxs-lookup"><span data-stu-id="1649f-125">SpinWait</span></span>](spinwait.md)|<span data-ttu-id="1649f-126">, Döndürme tabanlı bekleme desteği sağlayan <xref:System.Threading.SpinWait?displayProperty=nameWithType> yapısını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1649f-126">Describes the <xref:System.Threading.SpinWait?displayProperty=nameWithType> structure, which provides support for spin-based waiting.</span></span>|

## <a name="see-also"></a><span data-ttu-id="1649f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1649f-127">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [<span data-ttu-id="1649f-128">İş parçacıkları ve iş parçacığı kullanma</span><span class="sxs-lookup"><span data-stu-id="1649f-128">Using threads and threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="1649f-129">Zaman Uyumsuz Dosya G/Ç</span><span class="sxs-lookup"><span data-stu-id="1649f-129">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)
- [<span data-ttu-id="1649f-130">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="1649f-130">Parallel Programming</span></span>](../parallel-programming/index.md)
- [<span data-ttu-id="1649f-131">Görev Paralel Kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="1649f-131">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)
