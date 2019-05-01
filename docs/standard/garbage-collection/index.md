---
title: Çöp Toplama
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f61b63f78ea3c6131d4d1ab4e421be25149035b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931542"
---
# <a name="garbage-collection"></a><span data-ttu-id="693e9-102">Çöp Toplama</span><span class="sxs-lookup"><span data-stu-id="693e9-102">Garbage Collection</span></span>
<span data-ttu-id="693e9-103">. NET çöp toplayıcı ayrılmasını ve uygulamanız için bellek serbest yönetir.</span><span class="sxs-lookup"><span data-stu-id="693e9-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="693e9-104">Yeni bir nesne oluşturduğunuzda ortak dil çalışma zamanı, yönetilen yığından nesne için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="693e9-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="693e9-105">Yönetilen yığında kullanılabilir adres alanı bulunduğu sürece, çalışma zamanı yeni nesneler için bellek ayırmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="693e9-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="693e9-106">Ancak, bellek sonsuz değildir.</span><span class="sxs-lookup"><span data-stu-id="693e9-106">However, memory is not infinite.</span></span> <span data-ttu-id="693e9-107">Bir süre sonra, atık toplayıcısının bellekte yer açmak için bir toplama işlemi gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="693e9-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="693e9-108">Atık toplayıcısının iyileştirme altyapısı, yapılan bellek ayrımlarına göre bir toplama işlemi gerçekleştirmek için en iyi zamanı belirler.</span><span class="sxs-lookup"><span data-stu-id="693e9-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="693e9-109">Atık toplayıcı bir toplama işlemi gerçekleştirdiğinde, yönetilen yığın içinde uygulama tarafından artık kullanılmayan nesneleri denetler ve bu nesnelerin kullandığı belleği geri kazanmak için gerekli işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="693e9-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="693e9-110">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="693e9-110">Related Topics</span></span>  
  
|<span data-ttu-id="693e9-111">Başlık</span><span class="sxs-lookup"><span data-stu-id="693e9-111">Title</span></span>|<span data-ttu-id="693e9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="693e9-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="693e9-113">Atık Toplamanın Temelleri</span><span class="sxs-lookup"><span data-stu-id="693e9-113">Fundamentals of Garbage Collection</span></span>](../../../docs/standard/garbage-collection/fundamentals.md)|<span data-ttu-id="693e9-114">Atık toplamanın nasıl çalıştığını, nesnelere yönetilen yığında nasıl bellek ayrıldığını ve diğer temel kavramları açıklar.</span><span class="sxs-lookup"><span data-stu-id="693e9-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="693e9-115">Atık Toplama ve Performans</span><span class="sxs-lookup"><span data-stu-id="693e9-115">Garbage Collection and Performance</span></span>](../../../docs/standard/garbage-collection/performance.md)|<span data-ttu-id="693e9-116">Atık toplama ve performans sorunlarını tanılamak için kullanabileceğiniz performans denetimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="693e9-116">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="693e9-117">Uyarılmış Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="693e9-117">Induced Collections</span></span>](../../../docs/standard/garbage-collection/induced.md)|<span data-ttu-id="693e9-118">Bir atık toplama işleminin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="693e9-118">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="693e9-119">Gecikme Modları</span><span class="sxs-lookup"><span data-stu-id="693e9-119">Latency Modes</span></span>](../../../docs/standard/garbage-collection/latency.md)|<span data-ttu-id="693e9-120">Atık toplama işleminin ne kadar zorlayıcı olduğunu belirleyen modları açıklar.</span><span class="sxs-lookup"><span data-stu-id="693e9-120">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="693e9-121">Paylaşılan Web Barındırma için İyileştirme</span><span class="sxs-lookup"><span data-stu-id="693e9-121">Optimization for Shared Web Hosting</span></span>](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|<span data-ttu-id="693e9-122">Atık toplamanın birden çok küçük Web sitesi tarafından paylaşılan sunucularda nasıl iyileştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="693e9-122">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="693e9-123">Atık Toplama Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="693e9-123">Garbage Collection Notifications</span></span>](../../../docs/standard/garbage-collection/notifications.md)|<span data-ttu-id="693e9-124">Bir tam atık toplama işleminin yaklaşmakta olduğunun ve ne zaman tamamlandığının nasıl belirleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="693e9-124">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="693e9-125">Uygulama Etki Alanı Kaynak İzleme</span><span class="sxs-lookup"><span data-stu-id="693e9-125">Application Domain Resource Monitoring</span></span>](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|<span data-ttu-id="693e9-126">Bir uygulama etki alanının CPU ve bellek kullanımının nasıl izleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="693e9-126">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="693e9-127">Zayıf Başvurular</span><span class="sxs-lookup"><span data-stu-id="693e9-127">Weak References</span></span>](../../../docs/standard/garbage-collection/weak-references.md)|<span data-ttu-id="693e9-128">Atık toplayıcının, uygulamanın bir nesneye erişmesine hala izin verirken o nesneyi toplamasına olanak sağlayan özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="693e9-128">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="693e9-129">Başvuru</span><span class="sxs-lookup"><span data-stu-id="693e9-129">Reference</span></span>  
 <xref:System.GC?displayProperty=nameWithType>  
  
 <xref:System.GCCollectionMode?displayProperty=nameWithType>  
  
 <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
  
 <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="693e9-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="693e9-130">See also</span></span>

- [<span data-ttu-id="693e9-131">Yönetilmeyen Kaynakları Temizleme</span><span class="sxs-lookup"><span data-stu-id="693e9-131">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
