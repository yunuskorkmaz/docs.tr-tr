---
title: .NET çöp toplama
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
ms.openlocfilehash: c087deb033a373dd8b3980feb7ec6901c7909569
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102248"
---
# <a name="garbage-collection"></a><span data-ttu-id="14ea9-102">Atık toplama</span><span class="sxs-lookup"><span data-stu-id="14ea9-102">Garbage collection</span></span>

<span data-ttu-id="14ea9-103">. NET'in çöp toplayıcısı, uygulamanız için bellek tahsisini ve serbest bırakılmasını yönetir.</span><span class="sxs-lookup"><span data-stu-id="14ea9-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="14ea9-104">Yeni bir nesne oluşturduğunuzda ortak dil çalışma zamanı, yönetilen yığından nesne için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="14ea9-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="14ea9-105">Yönetilen yığında kullanılabilir adres alanı bulunduğu sürece, çalışma zamanı yeni nesneler için bellek ayırmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="14ea9-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="14ea9-106">Ancak, bellek sonsuz değildir.</span><span class="sxs-lookup"><span data-stu-id="14ea9-106">However, memory is not infinite.</span></span> <span data-ttu-id="14ea9-107">Bir süre sonra, atık toplayıcısının bellekte yer açmak için bir toplama işlemi gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="14ea9-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="14ea9-108">Atık toplayıcısının iyileştirme altyapısı, yapılan bellek ayrımlarına göre bir toplama işlemi gerçekleştirmek için en iyi zamanı belirler.</span><span class="sxs-lookup"><span data-stu-id="14ea9-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="14ea9-109">Atık toplayıcı bir toplama işlemi gerçekleştirdiğinde, yönetilen yığın içinde uygulama tarafından artık kullanılmayan nesneleri denetler ve bu nesnelerin kullandığı belleği geri kazanmak için gerekli işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="14ea9-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14ea9-110">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="14ea9-110">In this section</span></span>
  
|<span data-ttu-id="14ea9-111">Başlık</span><span class="sxs-lookup"><span data-stu-id="14ea9-111">Title</span></span>|<span data-ttu-id="14ea9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14ea9-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="14ea9-113">Çöp toplamanın temelleri</span><span class="sxs-lookup"><span data-stu-id="14ea9-113">Fundamentals of garbage collection</span></span>](../../../docs/standard/garbage-collection/fundamentals.md)|<span data-ttu-id="14ea9-114">Atık toplamanın nasıl çalıştığını, nesnelere yönetilen yığında nasıl bellek ayrıldığını ve diğer temel kavramları açıklar.</span><span class="sxs-lookup"><span data-stu-id="14ea9-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="14ea9-115">İş istasyonu ve sunucu çöp toplama</span><span class="sxs-lookup"><span data-stu-id="14ea9-115">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="14ea9-116">İstemci uygulamaları için iş istasyonu çöp toplama ile sunucu uygulamaları için sunucu çöp toplama arasındaki farkları açıklar.</span><span class="sxs-lookup"><span data-stu-id="14ea9-116">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="14ea9-117">Arka plan çöp toplama</span><span class="sxs-lookup"><span data-stu-id="14ea9-117">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="14ea9-118">Nesil 2 koleksiyonu devam ederken nesil 0 ve 1 nesnelerinin toplanması olan arka plan çöp toplama açıklar.</span><span class="sxs-lookup"><span data-stu-id="14ea9-118">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="14ea9-119">Büyük nesne yığını</span><span class="sxs-lookup"><span data-stu-id="14ea9-119">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="14ea9-120">Büyük nesne yığınını (LOH) ve büyük nesnelerin çöp olarak nasıl toplandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="14ea9-120">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="14ea9-121">Çöp toplama ve performans</span><span class="sxs-lookup"><span data-stu-id="14ea9-121">Garbage collection and performance</span></span>](../../../docs/standard/garbage-collection/performance.md)|<span data-ttu-id="14ea9-122">Atık toplama ve performans sorunlarını tanılamak için kullanabileceğiniz performans denetimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="14ea9-122">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="14ea9-123">Uyarılmış koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="14ea9-123">Induced collections</span></span>](../../../docs/standard/garbage-collection/induced.md)|<span data-ttu-id="14ea9-124">Bir atık toplama işleminin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="14ea9-124">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="14ea9-125">Gecikme modları</span><span class="sxs-lookup"><span data-stu-id="14ea9-125">Latency modes</span></span>](../../../docs/standard/garbage-collection/latency.md)|<span data-ttu-id="14ea9-126">Atık toplama işleminin ne kadar zorlayıcı olduğunu belirleyen modları açıklar.</span><span class="sxs-lookup"><span data-stu-id="14ea9-126">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="14ea9-127">Paylaşılan web barındırma için iyileştirme</span><span class="sxs-lookup"><span data-stu-id="14ea9-127">Optimization for shared web hosting</span></span>](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|<span data-ttu-id="14ea9-128">Atık toplamanın birden çok küçük Web sitesi tarafından paylaşılan sunucularda nasıl iyileştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="14ea9-128">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="14ea9-129">Çöp toplama bildirimleri</span><span class="sxs-lookup"><span data-stu-id="14ea9-129">Garbage collection notifications</span></span>](../../../docs/standard/garbage-collection/notifications.md)|<span data-ttu-id="14ea9-130">Bir tam atık toplama işleminin yaklaşmakta olduğunun ve ne zaman tamamlandığının nasıl belirleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="14ea9-130">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="14ea9-131">Uygulama etki alanı kaynak izleme</span><span class="sxs-lookup"><span data-stu-id="14ea9-131">Application domain resource monitoring</span></span>](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|<span data-ttu-id="14ea9-132">Bir uygulama etki alanının CPU ve bellek kullanımının nasıl izleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="14ea9-132">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="14ea9-133">Zayıf başvurular</span><span class="sxs-lookup"><span data-stu-id="14ea9-133">Weak references</span></span>](../../../docs/standard/garbage-collection/weak-references.md)|<span data-ttu-id="14ea9-134">Atık toplayıcının, uygulamanın bir nesneye erişmesine hala izin verirken o nesneyi toplamasına olanak sağlayan özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="14ea9-134">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="14ea9-135">Başvuru</span><span class="sxs-lookup"><span data-stu-id="14ea9-135">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="14ea9-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14ea9-136">See also</span></span>

- [<span data-ttu-id="14ea9-137">Yönetilmeyen kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="14ea9-137">Clean up unmanaged resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
