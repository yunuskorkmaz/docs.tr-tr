---
title: .NET atık toplama
ms.date: 04/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
ms.openlocfilehash: ef7e078c6ef2f0b4081c49aa0db09316e79f0702
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286060"
---
# <a name="garbage-collection"></a><span data-ttu-id="600d8-102">Atık toplama</span><span class="sxs-lookup"><span data-stu-id="600d8-102">Garbage collection</span></span>

<span data-ttu-id="600d8-103">. NET ' in atık toplayıcısı, uygulamanız için bellek ayırmayı ve serbest bırakma işlemini yönetir.</span><span class="sxs-lookup"><span data-stu-id="600d8-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="600d8-104">Yeni bir nesne oluşturduğunuzda ortak dil çalışma zamanı, yönetilen yığından nesne için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="600d8-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="600d8-105">Yönetilen yığında kullanılabilir adres alanı bulunduğu sürece, çalışma zamanı yeni nesneler için bellek ayırmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="600d8-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="600d8-106">Ancak, bellek sonsuz değildir.</span><span class="sxs-lookup"><span data-stu-id="600d8-106">However, memory is not infinite.</span></span> <span data-ttu-id="600d8-107">Bir süre sonra, atık toplayıcısının bellekte yer açmak için bir toplama işlemi gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="600d8-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="600d8-108">Atık toplayıcısının iyileştirme altyapısı, yapılan bellek ayrımlarına göre bir toplama işlemi gerçekleştirmek için en iyi zamanı belirler.</span><span class="sxs-lookup"><span data-stu-id="600d8-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="600d8-109">Atık toplayıcı bir toplama işlemi gerçekleştirdiğinde, yönetilen yığın içinde uygulama tarafından artık kullanılmayan nesneleri denetler ve bu nesnelerin kullandığı belleği geri kazanmak için gerekli işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="600d8-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="600d8-110">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="600d8-110">In this section</span></span>
  
|<span data-ttu-id="600d8-111">Başlık</span><span class="sxs-lookup"><span data-stu-id="600d8-111">Title</span></span>|<span data-ttu-id="600d8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="600d8-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="600d8-113">Çöp toplamanın temelleri</span><span class="sxs-lookup"><span data-stu-id="600d8-113">Fundamentals of garbage collection</span></span>](fundamentals.md)|<span data-ttu-id="600d8-114">Atık toplamanın nasıl çalıştığını, nesnelere yönetilen yığında nasıl bellek ayrıldığını ve diğer temel kavramları açıklar.</span><span class="sxs-lookup"><span data-stu-id="600d8-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="600d8-115">İş istasyonu ve sunucu atık toplama</span><span class="sxs-lookup"><span data-stu-id="600d8-115">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="600d8-116">İstemci uygulamaları için iş istasyonu atık toplama ve sunucu uygulamaları için sunucu çöp toplama arasındaki farkları açıklar.</span><span class="sxs-lookup"><span data-stu-id="600d8-116">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="600d8-117">Arka plan atık toplama</span><span class="sxs-lookup"><span data-stu-id="600d8-117">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="600d8-118">2. nesil toplama işlemi devam ederken, nesil 0 ve 1 nesnelerinin toplanması olan arka plan çöp toplama işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="600d8-118">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="600d8-119">Büyük nesne yığını</span><span class="sxs-lookup"><span data-stu-id="600d8-119">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="600d8-120">Büyük nesne yığınını (LOH) ve büyük nesneleri atık toplanan olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="600d8-120">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="600d8-121">Çöp toplama ve performans</span><span class="sxs-lookup"><span data-stu-id="600d8-121">Garbage collection and performance</span></span>](performance.md)|<span data-ttu-id="600d8-122">Atık toplama ve performans sorunlarını tanılamak için kullanabileceğiniz performans denetimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="600d8-122">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="600d8-123">Uyarılmış koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="600d8-123">Induced collections</span></span>](induced.md)|<span data-ttu-id="600d8-124">Bir atık toplama işleminin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="600d8-124">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="600d8-125">Gecikme modları</span><span class="sxs-lookup"><span data-stu-id="600d8-125">Latency modes</span></span>](latency.md)|<span data-ttu-id="600d8-126">Atık toplama işleminin ne kadar zorlayıcı olduğunu belirleyen modları açıklar.</span><span class="sxs-lookup"><span data-stu-id="600d8-126">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="600d8-127">Paylaşılan web barındırma için iyileştirme</span><span class="sxs-lookup"><span data-stu-id="600d8-127">Optimization for shared web hosting</span></span>](optimization-for-shared-web-hosting.md)|<span data-ttu-id="600d8-128">Atık toplamanın birden çok küçük Web sitesi tarafından paylaşılan sunucularda nasıl iyileştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="600d8-128">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="600d8-129">Çöp toplama bildirimleri</span><span class="sxs-lookup"><span data-stu-id="600d8-129">Garbage collection notifications</span></span>](notifications.md)|<span data-ttu-id="600d8-130">Bir tam atık toplama işleminin yaklaşmakta olduğunun ve ne zaman tamamlandığının nasıl belirleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="600d8-130">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="600d8-131">Uygulama etki alanı kaynak izleme</span><span class="sxs-lookup"><span data-stu-id="600d8-131">Application domain resource monitoring</span></span>](app-domain-resource-monitoring.md)|<span data-ttu-id="600d8-132">Bir uygulama etki alanının CPU ve bellek kullanımının nasıl izleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="600d8-132">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="600d8-133">Zayıf başvurular</span><span class="sxs-lookup"><span data-stu-id="600d8-133">Weak references</span></span>](weak-references.md)|<span data-ttu-id="600d8-134">Atık toplayıcının, uygulamanın bir nesneye erişmesine hala izin verirken o nesneyi toplamasına olanak sağlayan özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="600d8-134">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="600d8-135">Başvuru</span><span class="sxs-lookup"><span data-stu-id="600d8-135">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="600d8-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="600d8-136">See also</span></span>

- [<span data-ttu-id="600d8-137">Yönetilmeyen kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="600d8-137">Clean up unmanaged resources</span></span>](unmanaged.md)
