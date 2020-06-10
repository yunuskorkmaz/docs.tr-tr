---
title: .NET atık toplama
description: .NET 'teki çöp toplama hakkında bilgi edinin. .NET atık toplayıcısı, uygulamanız için bellek ayırmayı ve serbest bırakma işlemini yönetir.
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
ms.openlocfilehash: dde0012ff7233eb7ee13efab1931f129b0eae276
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662491"
---
# <a name="garbage-collection"></a><span data-ttu-id="ca421-104">Atık toplama</span><span class="sxs-lookup"><span data-stu-id="ca421-104">Garbage collection</span></span>

<span data-ttu-id="ca421-105">. NET ' in atık toplayıcısı, uygulamanız için bellek ayırmayı ve serbest bırakma işlemini yönetir.</span><span class="sxs-lookup"><span data-stu-id="ca421-105">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="ca421-106">Yeni bir nesne oluşturduğunuzda ortak dil çalışma zamanı, yönetilen yığından nesne için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="ca421-106">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="ca421-107">Yönetilen yığında kullanılabilir adres alanı bulunduğu sürece, çalışma zamanı yeni nesneler için bellek ayırmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="ca421-107">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="ca421-108">Ancak, bellek sonsuz değildir.</span><span class="sxs-lookup"><span data-stu-id="ca421-108">However, memory is not infinite.</span></span> <span data-ttu-id="ca421-109">Bir süre sonra, atık toplayıcısının bellekte yer açmak için bir toplama işlemi gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca421-109">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="ca421-110">Atık toplayıcısının iyileştirme altyapısı, yapılan bellek ayrımlarına göre bir toplama işlemi gerçekleştirmek için en iyi zamanı belirler.</span><span class="sxs-lookup"><span data-stu-id="ca421-110">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="ca421-111">Atık toplayıcı bir toplama işlemi gerçekleştirdiğinde, yönetilen yığın içinde uygulama tarafından artık kullanılmayan nesneleri denetler ve bu nesnelerin kullandığı belleği geri kazanmak için gerekli işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ca421-111">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ca421-112">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="ca421-112">In this section</span></span>
  
|<span data-ttu-id="ca421-113">Başlık</span><span class="sxs-lookup"><span data-stu-id="ca421-113">Title</span></span>|<span data-ttu-id="ca421-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca421-114">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ca421-115">Çöp toplamanın temelleri</span><span class="sxs-lookup"><span data-stu-id="ca421-115">Fundamentals of garbage collection</span></span>](fundamentals.md)|<span data-ttu-id="ca421-116">Atık toplamanın nasıl çalıştığını, nesnelere yönetilen yığında nasıl bellek ayrıldığını ve diğer temel kavramları açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca421-116">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="ca421-117">İş istasyonu ve sunucu atık toplama</span><span class="sxs-lookup"><span data-stu-id="ca421-117">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="ca421-118">İstemci uygulamaları için iş istasyonu atık toplama ve sunucu uygulamaları için sunucu çöp toplama arasındaki farkları açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca421-118">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="ca421-119">Arka plan atık toplama</span><span class="sxs-lookup"><span data-stu-id="ca421-119">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="ca421-120">2. nesil toplama işlemi devam ederken, nesil 0 ve 1 nesnelerinin toplanması olan arka plan çöp toplama işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca421-120">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="ca421-121">Büyük nesne yığını</span><span class="sxs-lookup"><span data-stu-id="ca421-121">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="ca421-122">Büyük nesne yığınını (LOH) ve büyük nesneleri atık toplanan olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ca421-122">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="ca421-123">Çöp toplama ve performans</span><span class="sxs-lookup"><span data-stu-id="ca421-123">Garbage collection and performance</span></span>](performance.md)|<span data-ttu-id="ca421-124">Atık toplama ve performans sorunlarını tanılamak için kullanabileceğiniz performans denetimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca421-124">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="ca421-125">Uyarılmış koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="ca421-125">Induced collections</span></span>](induced.md)|<span data-ttu-id="ca421-126">Bir atık toplama işleminin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca421-126">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="ca421-127">Gecikme modları</span><span class="sxs-lookup"><span data-stu-id="ca421-127">Latency modes</span></span>](latency.md)|<span data-ttu-id="ca421-128">Atık toplama işleminin ne kadar zorlayıcı olduğunu belirleyen modları açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca421-128">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="ca421-129">Paylaşılan web barındırma için iyileştirme</span><span class="sxs-lookup"><span data-stu-id="ca421-129">Optimization for shared web hosting</span></span>](optimization-for-shared-web-hosting.md)|<span data-ttu-id="ca421-130">Atık toplamanın birden çok küçük Web sitesi tarafından paylaşılan sunucularda nasıl iyileştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca421-130">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="ca421-131">Çöp toplama bildirimleri</span><span class="sxs-lookup"><span data-stu-id="ca421-131">Garbage collection notifications</span></span>](notifications.md)|<span data-ttu-id="ca421-132">Bir tam atık toplama işleminin yaklaşmakta olduğunun ve ne zaman tamamlandığının nasıl belirleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca421-132">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="ca421-133">Uygulama etki alanı kaynak izleme</span><span class="sxs-lookup"><span data-stu-id="ca421-133">Application domain resource monitoring</span></span>](app-domain-resource-monitoring.md)|<span data-ttu-id="ca421-134">Bir uygulama etki alanının CPU ve bellek kullanımının nasıl izleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca421-134">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="ca421-135">Zayıf başvurular</span><span class="sxs-lookup"><span data-stu-id="ca421-135">Weak references</span></span>](weak-references.md)|<span data-ttu-id="ca421-136">Atık toplayıcının, uygulamanın bir nesneye erişmesine hala izin verirken o nesneyi toplamasına olanak sağlayan özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca421-136">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="ca421-137">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ca421-137">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="ca421-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca421-138">See also</span></span>

- [<span data-ttu-id="ca421-139">Yönetilmeyen kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="ca421-139">Clean up unmanaged resources</span></span>](unmanaged.md)
