---
title: İş istasyonu ve sunucu çöp toplama (GC)
description: .NET'te iş istasyonu ve sunucu çöp toplama hakkında bilgi edinin.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 6b8e5f6802e5d44669b95d43d4e897fa4a418512
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103557"
---
# <a name="workstation-and-server-garbage-collection"></a><span data-ttu-id="8a894-103">İş istasyonu ve sunucu çöp toplama</span><span class="sxs-lookup"><span data-stu-id="8a894-103">Workstation and server garbage collection</span></span>

<span data-ttu-id="8a894-104">Çöp toplayıcı kendi kendini ayarlıyor ve çok çeşitli senaryolarda çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="8a894-104">The garbage collector is self-tuning and can work in a wide variety of scenarios.</span></span> <span data-ttu-id="8a894-105">Ancak, [iş yükünün](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) özelliklerine göre çöp toplama türünü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a894-105">However, you can [set the type of garbage collection](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) based on the characteristics of the workload.</span></span> <span data-ttu-id="8a894-106">CLR aşağıdaki çöp toplama türlerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="8a894-106">The CLR provides the following types of garbage collection:</span></span>

- <span data-ttu-id="8a894-107">İstemci uygulamaları için tasarlanmış iş istasyonu çöp toplama (GC).</span><span class="sxs-lookup"><span data-stu-id="8a894-107">Workstation garbage collection (GC), which is designed for client apps.</span></span> <span data-ttu-id="8a894-108">Bağımsız uygulamalar için varsayılan GC tadıdır.</span><span class="sxs-lookup"><span data-stu-id="8a894-108">It's the default GC flavor for standalone apps.</span></span> <span data-ttu-id="8a894-109">Barındırılan uygulamalar için, örneğin, ASP.NET tarafından barındırılan uygulamalar için, ana bilgisayar varsayılan GC lezzetini belirler.</span><span class="sxs-lookup"><span data-stu-id="8a894-109">For hosted apps, for example, those hosted by ASP.NET, the host determines the default GC flavor.</span></span>

  <span data-ttu-id="8a894-110">İş istasyonu çöp toplama eşzamanlı veya eşzamanlı olmayan olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a894-110">Workstation garbage collection can be concurrent or non-concurrent.</span></span> <span data-ttu-id="8a894-111">Eşzamanlı (veya *arka plan)* çöp toplama, yönetilen iş parçacıklarının çöp toplama sırasında işlemlerine devam etmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a894-111">Concurrent (or *background*) garbage collection enables managed threads to continue operations during a garbage collection.</span></span> <span data-ttu-id="8a894-112">[Arka plan çöp toplama](background-gc.md) ,NET Framework 4 ve sonraki sürümlerde [eşzamanlı çöp toplama](background-gc.md#concurrent-garbage-collection) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8a894-112">[Background garbage collection](background-gc.md) replaces [concurrent garbage collection](background-gc.md#concurrent-garbage-collection) in .NET Framework 4 and later versions.</span></span>

- <span data-ttu-id="8a894-113">Yüksek iş gücü ve ölçeklenebilirlik gerektiren sunucu uygulamaları için tasarlanmış sunucu çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="8a894-113">Server garbage collection, which is intended for server applications that need high throughput and scalability.</span></span>

  - <span data-ttu-id="8a894-114">.NET Core'da sunucu çöp toplama eşzamanlı olmayan veya arka plan olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a894-114">In .NET Core, server garbage collection can be non-concurrent or background.</span></span>

  - <span data-ttu-id="8a894-115">.NET Framework 4.5 ve sonraki sürümlerde sunucu çöp toplama eşzamanlı olmayan veya arka plan olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a894-115">In .NET Framework 4.5 and later versions, server garbage collection can be non-concurrent or background.</span></span> <span data-ttu-id="8a894-116">.NET Framework 4 ve önceki sürümlerde sunucu çöp toplama eşzamanlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8a894-116">In .NET Framework 4 and previous versions, server garbage collection is non-concurrent.</span></span>

<span data-ttu-id="8a894-117">Aşağıdaki resimde, bir sunucuda çöp toplama işlemini gerçekleştiren özel iş parçacıkları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8a894-117">The following illustration shows the dedicated threads that perform the garbage collection on a server:</span></span>

![Sunucu Çöp Toplama İş parçacıkları](./media/gc-server.png)

## <a name="performance-considerations"></a><span data-ttu-id="8a894-119">Performansla ilgili önemli noktalar</span><span class="sxs-lookup"><span data-stu-id="8a894-119">Performance considerations</span></span>

### <a name="workstation-gc"></a><span data-ttu-id="8a894-120">İş istasyonu GC</span><span class="sxs-lookup"><span data-stu-id="8a894-120">Workstation GC</span></span>

<span data-ttu-id="8a894-121">İş istasyonu çöp toplama için iş parçacığı ve performans hususları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8a894-121">The following are threading and performance considerations for workstation garbage collection:</span></span>

- <span data-ttu-id="8a894-122">Koleksiyon, çöp toplamayı tetikleyen kullanıcı iş parçacığında oluşur ve aynı öncelikte kalır.</span><span class="sxs-lookup"><span data-stu-id="8a894-122">The collection occurs on the user thread that triggered the garbage collection and remains at the same priority.</span></span> <span data-ttu-id="8a894-123">Kullanıcı iş parçacıkları genellikle normal öncelikte çalıştığından, çöp toplayıcı (normal bir öncelik iş parçacığı üzerinde çalışır) CPU süresi için diğer iş parçacıkları ile rekabet etmelidir.</span><span class="sxs-lookup"><span data-stu-id="8a894-123">Because user threads typically run at normal priority, the garbage collector (which runs on a normal priority thread) must compete with other threads for CPU time.</span></span> <span data-ttu-id="8a894-124">(Yerel kodu çalıştıran iş parçacıkları sunucu veya iş istasyonu çöp toplama da askıya alınmaz.)</span><span class="sxs-lookup"><span data-stu-id="8a894-124">(Threads that run native code are not suspended on either server or workstation garbage collection.)</span></span>

- <span data-ttu-id="8a894-125">İş istasyonu çöp toplama, [yapılandırma ayarından](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)bağımsız olarak her zaman yalnızca bir işlemciye sahip bir bilgisayarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8a894-125">Workstation garbage collection is always used on a computer that has only one processor, regardless of the [configuration setting](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

### <a name="server-gc"></a><span data-ttu-id="8a894-126">Sunucu GC</span><span class="sxs-lookup"><span data-stu-id="8a894-126">Server GC</span></span>

<span data-ttu-id="8a894-127">Sunucu çöp toplama için iş parçacığı ve performans konuları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8a894-127">The following are threading and performance considerations for server garbage collection:</span></span>

- <span data-ttu-id="8a894-128">Koleksiyon, `THREAD_PRIORITY_HIGHEST` öncelik düzeyinde çalışan birden çok özel iş parçacığı üzerinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="8a894-128">The collection occurs on multiple dedicated threads that are running at `THREAD_PRIORITY_HIGHEST` priority level.</span></span>

- <span data-ttu-id="8a894-129">Her CPU için çöp toplama yapmak için bir yığın ve özel bir iş parçacığı sağlanır ve yığınlar aynı anda toplanır.</span><span class="sxs-lookup"><span data-stu-id="8a894-129">A heap and a dedicated thread to perform garbage collection are provided for each CPU, and the heaps are collected at the same time.</span></span> <span data-ttu-id="8a894-130">Her yığın küçük bir nesne yığını ve büyük bir nesne yığını içerir ve tüm yığınlara kullanıcı koduyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="8a894-130">Each heap contains a small object heap and a large object heap, and all heaps can be accessed by user code.</span></span> <span data-ttu-id="8a894-131">Farklı yığınlar üzerindeki nesneler birbirine başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="8a894-131">Objects on different heaps can refer to each other.</span></span>

- <span data-ttu-id="8a894-132">Birden çok çöp toplama iş parçacığı birlikte çalıştığıiçin, sunucu çöp toplama aynı boyuttaki yığındaki iş istasyonu çöp toplama işleminden daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="8a894-132">Because multiple garbage collection threads work together, server garbage collection is faster than workstation garbage collection on the same size heap.</span></span>

- <span data-ttu-id="8a894-133">Sunucu çöp toplama genellikle daha büyük boyutlu segmentleri vardır.</span><span class="sxs-lookup"><span data-stu-id="8a894-133">Server garbage collection often has larger size segments.</span></span> <span data-ttu-id="8a894-134">Ancak, bu yalnızca bir genellemedir: segment boyutu uygulamaya özgüdür ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8a894-134">However, this is only a generalization: segment size is implementation-specific and is subject to change.</span></span> <span data-ttu-id="8a894-135">Uygulamanızı alarken çöp toplayıcıtarafından ayrılan segmentlerin boyutu hakkında varsayımlarda bulunmayın.</span><span class="sxs-lookup"><span data-stu-id="8a894-135">Don't make assumptions about the size of segments allocated by the garbage collector when tuning your app.</span></span>

- <span data-ttu-id="8a894-136">Sunucu çöp toplama kaynak yoğun olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a894-136">Server garbage collection can be resource-intensive.</span></span> <span data-ttu-id="8a894-137">Örneğin, dört işlemcisi olan bir bilgisayarda çalışan sunucu GC kullanan 12 işlem olduğunu düşünün.</span><span class="sxs-lookup"><span data-stu-id="8a894-137">For example, imagine that there are 12 processes that use server GC running on a computer that has four processors.</span></span> <span data-ttu-id="8a894-138">Tüm işlemler aynı anda çöp toplamak için olur, onlar birbirlerine müdahale olur, aynı işlemci üzerinde zamanlanmış 12 iş parçacığı olurdu.</span><span class="sxs-lookup"><span data-stu-id="8a894-138">If all the processes happen to collect garbage at the same time, they would interfere with each other, as there would be 12 threads scheduled on the same processor.</span></span> <span data-ttu-id="8a894-139">İşlemler etkinse, hepsinin sunucu GC'sini kullanmasını sağlamak iyi bir fikir değildir.</span><span class="sxs-lookup"><span data-stu-id="8a894-139">If the processes are active, it's not a good idea to have them all use server GC.</span></span>

<span data-ttu-id="8a894-140">Bir uygulamanın yüzlerce örneğini çalıştırıyorsanız, eşzamanlı çöp toplama devre dışı bırakılmış iş istasyonu çöp toplama kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="8a894-140">If you're running hundreds of instances of an application, consider using workstation garbage collection with concurrent garbage collection disabled.</span></span> <span data-ttu-id="8a894-141">Bu, performansı artırabilecek daha az bağlam geçişine neden olur.</span><span class="sxs-lookup"><span data-stu-id="8a894-141">This will result in less context switching, which can improve performance.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a894-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a894-142">See also</span></span>

- [<span data-ttu-id="8a894-143">Arka plan çöp toplama</span><span class="sxs-lookup"><span data-stu-id="8a894-143">Background garbage collection</span></span>](background-gc.md)
- [<span data-ttu-id="8a894-144">Çöp toplama için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8a894-144">Run-time configuration options for garbage collection</span></span>](../../core/run-time-config/garbage-collector.md)
