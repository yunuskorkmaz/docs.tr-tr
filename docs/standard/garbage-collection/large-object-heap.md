---
title: Windows üzerinde büyük nesne yığını (LOH)
description: Bu makalede büyük nesneler, .NET atık toplayıcısı tarafından nasıl yönetildiği ve büyük nesneleri kullanmanın performans etkileri anlatılmaktadır.
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: dae8a3690d63d77a47a5cd2e76f210ca8210f058
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420584"
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="2b890-103">Windows sistemlerinde büyük nesne yığını</span><span class="sxs-lookup"><span data-stu-id="2b890-103">The large object heap on Windows systems</span></span>

<span data-ttu-id="2b890-104">.NET çöp toplayıcı (GC), nesneleri küçük ve büyük nesnelere böler.</span><span class="sxs-lookup"><span data-stu-id="2b890-104">The .NET garbage collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="2b890-105">Bir nesne büyükse, bazı öznitelikleri nesnenin küçük olmasına göre daha önemli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="2b890-105">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="2b890-106">Örneğin, bunu sıkıştırmak, &mdash; başka bir yere yığın üzerine kopyalamak &mdash; pahalı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-106">For instance, compacting it&mdash;that is, copying it in memory elsewhere on the heap&mdash;can be expensive.</span></span> <span data-ttu-id="2b890-107">Bu nedenle, atık toplayıcı büyük nesne yığınına (LOH) büyük nesneler koyar.</span><span class="sxs-lookup"><span data-stu-id="2b890-107">Because of this, the garbage collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="2b890-108">Bu makalede, bir nesneyi büyük bir nesne olarak niteleyen, büyük nesnelerin nasıl toplandığı ve büyük nesnelerin ne tür performans etkilerine yönelik olduğunu ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b890-108">This article discusses what qualifies an object as a large object, how large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2b890-109">Bu makalede, yalnızca Windows sistemlerinde çalışan .NET Framework ve .NET Core 'daki büyük nesne yığını ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b890-109">This article discusses the large object heap in .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="2b890-110">Diğer platformlarda .NET uygulamalarında çalışan LOH 'yi kapsamaz.</span><span class="sxs-lookup"><span data-stu-id="2b890-110">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-loh"></a><span data-ttu-id="2b890-111">Bir nesne LOH üzerinde nasıl sona eriyor</span><span class="sxs-lookup"><span data-stu-id="2b890-111">How an object ends up on the LOH</span></span>

<span data-ttu-id="2b890-112">Bir nesne boyut olarak 85.000 bayttan büyükse veya eşitse, büyük bir nesne olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-112">If an object is greater than or equal to 85,000 bytes in size, it’s considered a large object.</span></span> <span data-ttu-id="2b890-113">Bu sayı performans ayarlaması tarafından belirlendi.</span><span class="sxs-lookup"><span data-stu-id="2b890-113">This number was determined by performance tuning.</span></span> <span data-ttu-id="2b890-114">Bir nesne ayırma isteği 85.000 veya daha fazla bayt için olduğunda, çalışma zamanı onu büyük nesne yığınında ayırır.</span><span class="sxs-lookup"><span data-stu-id="2b890-114">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="2b890-115">Bunun ne anlama geldiğini anlamak için, atık toplayıcıyla ilgili bazı temelleri incelemek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="2b890-115">To understand what this means, it's useful to examine some fundamentals about the garbage collector.</span></span>

<span data-ttu-id="2b890-116">Çöp toplayıcı, bir genel toplayıcı.</span><span class="sxs-lookup"><span data-stu-id="2b890-116">The garbage collector is a generational collector.</span></span> <span data-ttu-id="2b890-117">Üç nesle sahiptir: nesil 0, 1. nesil ve 2. nesil.</span><span class="sxs-lookup"><span data-stu-id="2b890-117">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="2b890-118">3 nesin olmasının nedeni, iyi ayarlanmış bir uygulamada, çoğu nesne gen0 ' de zar.</span><span class="sxs-lookup"><span data-stu-id="2b890-118">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="2b890-119">Örneğin, bir sunucu uygulamasında her bir istekle ilişkili ayırmalar istek bittikten sonra zar almalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b890-119">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="2b890-120">Uçuş aşamasında ayırma istekleri bunu gen1 ve zar alacak şekilde yapar.</span><span class="sxs-lookup"><span data-stu-id="2b890-120">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="2b890-121">Temelde, Gen1 küçük nesne alanlarıyla uzun süreli nesne alanı arasında bir arabellek işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="2b890-121">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="2b890-122">Küçük nesneler her zaman 0. kuşak olarak ayrılır ve yaşam süresine bağlı olarak 1. veya generation2 sürümüne yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-122">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="2b890-123">Büyük nesneler her zaman 2. nesil olarak ayrılır.</span><span class="sxs-lookup"><span data-stu-id="2b890-123">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="2b890-124">Büyük nesneler yalnızca 2. nesil bir koleksiyon sırasında toplandıklarından 2. nesil için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2b890-124">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="2b890-125">Bir oluşturma toplandığında, tüm küçük oluşturma öğeleri de toplanır.</span><span class="sxs-lookup"><span data-stu-id="2b890-125">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="2b890-126">Örneğin, 1. nesil bir GC gerçekleştiğinde hem 1. kuşak hem de 0 toplanır.</span><span class="sxs-lookup"><span data-stu-id="2b890-126">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="2b890-127">2. nesil GC gerçekleştiğinde, tüm yığın toplanır.</span><span class="sxs-lookup"><span data-stu-id="2b890-127">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="2b890-128">Bu nedenle, 2. nesil GC 'nin *tam GC*olarak da denir.</span><span class="sxs-lookup"><span data-stu-id="2b890-128">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="2b890-129">Bu makale, tam GC yerine 2. nesil GC 'ye başvurur, ancak şartlar aynı şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-129">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="2b890-130">Nesiller, GC yığınının mantıksal bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b890-130">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="2b890-131">Fiziksel olarak, nesneler yönetilen yığın kesimlerinde bulunurlar.</span><span class="sxs-lookup"><span data-stu-id="2b890-131">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="2b890-132">*Yönetilen bir yığın segmenti* , yönetilen kod adına [VIRTUALALLOC işlevini](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) çağırarak GC 'nin işletim sisteminden ayrılmış bir bellek öbektir.</span><span class="sxs-lookup"><span data-stu-id="2b890-132">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) on behalf of managed code.</span></span> <span data-ttu-id="2b890-133">CLR yüklendiğinde, GC iki başlangıç yığın kesimini ayırır: biri küçük nesneler (küçük nesne yığını veya SOH) için, diğeri ise büyük nesneler için (büyük nesne yığını).</span><span class="sxs-lookup"><span data-stu-id="2b890-133">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the small object heap, or SOH), and one for large objects (the large object heap).</span></span>

<span data-ttu-id="2b890-134">Bu yönetilen yığın kesimlerinde yönetilen nesneler yerleştirilerek, ayırma istekleri karşılanır.</span><span class="sxs-lookup"><span data-stu-id="2b890-134">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="2b890-135">Nesne 85.000 bayttan küçükse, SOH için kesime konur; Aksi takdirde, bir LOH segmentine konur.</span><span class="sxs-lookup"><span data-stu-id="2b890-135">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="2b890-136">Bölümler, üzerinde daha fazla nesne ayrıldığından (daha küçük öbeklerde) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-136">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="2b890-137">SOH için, GC 'yi sürdüren nesneler bir sonraki oluşturmaya yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-137">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="2b890-138">Nesil 0 koleksiyonunu etkileyen nesneler artık 1. kuşak nesneler olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-138">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="2b890-139">Ancak, en eski üretimi sürdüren nesneler hala en eski nesil olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-139">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="2b890-140">Diğer bir deyişle 2. nesil, 2. nesil nesnelerdir. LOH 'den ve, LOH nesneleri (Gen2 ile toplanan).</span><span class="sxs-lookup"><span data-stu-id="2b890-140">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span>

<span data-ttu-id="2b890-141">Kullanıcı kodu yalnızca nesil 0 (küçük nesneler) veya LOH (büyük nesneler) halinde ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-141">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="2b890-142">Yalnızca GC, 1. nesil nesneleri "ayırabilir" (nesil 0 ' dan kalan VNET 'ler yükselterek) ve 2. nesil (nesilleri 1 ve 2 ' den yükseltmek için).</span><span class="sxs-lookup"><span data-stu-id="2b890-142">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="2b890-143">Bir çöp toplama tetiklendiğinde, GC canlı nesneler aracılığıyla izler ve bunları sıkıştırır.</span><span class="sxs-lookup"><span data-stu-id="2b890-143">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="2b890-144">Ancak, sıkıştırma pahalı olduğundan *, GC,* Loh; büyük nesne ayırma isteklerini karşılamak için daha sonra yeniden kullanılabilen, ölü nesnelerden ücretsiz bir liste oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2b890-144">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="2b890-145">Bitişik ölü nesneler tek bir ücretsiz nesne içinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="2b890-145">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="2b890-146">.NET Core ve .NET Framework (.NET Framework 4.5.1 ile başlayarak), <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> kullanıcıların bir sonraki tam engelleme GC sırasında LOH 'nin sıkıştırılması gerektiğini belirtmesini sağlayan özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="2b890-146">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="2b890-147">Daha sonra .NET, LOH 'yi otomatik olarak sıkıştırmak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-147">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="2b890-148">Bu, büyük nesneler tahsis ederseniz ve bunların taşınmadığından emin olmak istiyorsanız onları hala sabitlediğinizden emin olmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2b890-148">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="2b890-149">Şekil 1 ' de, GC formlarının ilk nesil 0 GC 'den sonra 1 ' in oluşturduğu ve `Obj1` `Obj3` ölü ve ilk nesıl 1 GC sonrasında 2 `Obj2` . nesil ve kapalı olduğu bir senaryo gösterilir `Obj5` .</span><span class="sxs-lookup"><span data-stu-id="2b890-149">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="2b890-150">Bu ve aşağıdaki rakamların yalnızca çizim amaçlarıyla olduğunu unutmayın; yığın üzerinde ne olacağını daha iyi göstermek için çok az nesne içerirler.</span><span class="sxs-lookup"><span data-stu-id="2b890-150">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="2b890-151">Gerçekte, genellikle bir GC 'ye dahil birçok nesne daha vardır.</span><span class="sxs-lookup"><span data-stu-id="2b890-151">In reality, many more objects are typically involved in a GC.</span></span>

![Şekil 1: bir gen 0 GC ve Gen 1 GC](media/loh/loh-figure-1.jpg)\
<span data-ttu-id="2b890-153">Şekil 1: nesil 0 ve 1. nesil GC.</span><span class="sxs-lookup"><span data-stu-id="2b890-153">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="2b890-154">Şekil 2 ' nin, ve ölü olduğunu belirten 2. nesil GC sonrasında `Obj1` `Obj2` , GC 'nin, `Obj1` ve `Obj2` için bir ayırma isteğini karşılamak için kullanılan bellek içi boş alan `Obj4` olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b890-154">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="2b890-155">Son nesneden sonra, `Obj3` segmentin sonuna kadar olan boşluk, ayırma isteklerini karşılamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-155">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>

![Şekil 2: bir gen 2 GC 'den sonra](media/loh/loh-figure-2.jpg)\
<span data-ttu-id="2b890-157">Şekil 2:2. nesil GC 'den sonra</span><span class="sxs-lookup"><span data-stu-id="2b890-157">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="2b890-158">Büyük nesne ayırma isteklerini barındırmak için yeterli boş alan yoksa, GC ilk olarak IŞLETIM sisteminden daha fazla kesim edinmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="2b890-158">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="2b890-159">Bu başarısız olursa, biraz alan boşaltmayı umuyoruz 2. nesil GC 'yi tetikler.</span><span class="sxs-lookup"><span data-stu-id="2b890-159">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="2b890-160">1. nesil veya 2. nesil GC sırasında, atık toplayıcı, [VirtualFree işlevini](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree)çağırarak işletim sistemlerinde canlı nesneleri olmayan kesimleri serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="2b890-160">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span></span> <span data-ttu-id="2b890-161">Segmentin sonuna kadar olan son canlı nesneden sonra gelen boşluk, (gen0/Gen1 Live 'un, uygulamanızın doğru bir şekilde ayrıldığı için çöp toplayıcısının bir süre önce tutulması durumunda) yürütüldüğünden çalışır.</span><span class="sxs-lookup"><span data-stu-id="2b890-161">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="2b890-162">Ve boş alanlar sıfırlansa da, bu da işletim sisteminin verileri diske geri yazmasına gerek olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2b890-162">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="2b890-163">LOH yalnızca 2. kuşak sırasında toplandığından, LOH segmenti yalnızca bu tür bir GC sırasında serbest bırakılabilirler.</span><span class="sxs-lookup"><span data-stu-id="2b890-163">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="2b890-164">Şekil 3 ' te, çöp toplayıcı 'nın bir kesimi (segment 2) işletim sistemine yeniden yayınlayıp kalan kesimlerde daha fazla alan yürütmelerinin bulunduğu bir senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2b890-164">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="2b890-165">Büyük nesne ayırma isteklerini karşılamak için segmentin sonunda, ayrılan alan seçimini kullanması gerekiyorsa, belleği yeniden kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2b890-165">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="2b890-166">(COMMIT/COMMIT hakkında bir açıklama için bkz. [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc)belgeleri.</span><span class="sxs-lookup"><span data-stu-id="2b890-166">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span></span>

![Şekil 3: Gen 2 GC sonrasında LOH](media/loh/loh-figure-3.jpg)\
<span data-ttu-id="2b890-168">Şekil 3:2. nesil GC sonrasında LOH</span><span class="sxs-lookup"><span data-stu-id="2b890-168">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="2b890-169">Büyük bir nesne ne zaman toplanır?</span><span class="sxs-lookup"><span data-stu-id="2b890-169">When is a large object collected?</span></span>

<span data-ttu-id="2b890-170">Genel olarak, aşağıdaki üç koşuldan biri altında bir GC oluşur:</span><span class="sxs-lookup"><span data-stu-id="2b890-170">In general, a GC occurs under one of the following three conditions:</span></span>

- <span data-ttu-id="2b890-171">Ayırma, 1. kuşak veya büyük nesne eşiğini aşıyor.</span><span class="sxs-lookup"><span data-stu-id="2b890-171">Allocation exceeds the generation 0 or large object threshold.</span></span>

  <span data-ttu-id="2b890-172">Eşik, oluşturma özelliğinin bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="2b890-172">The threshold is a property of a generation.</span></span> <span data-ttu-id="2b890-173">Atık toplayıcı nesneleri içine ayırdığı zaman oluşturma için bir eşik ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2b890-173">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="2b890-174">Eşik aşıldığında, bu Neste bir GC tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="2b890-174">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="2b890-175">Küçük veya büyük nesneler ayırdığınızda, 1. nesil ve LOH 'nin eşiklerini sırasıyla kullanın.</span><span class="sxs-lookup"><span data-stu-id="2b890-175">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="2b890-176">Çöp toplayıcı 1. ve 2. kuşak olarak tahsis edildiğinde, eşiklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b890-176">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="2b890-177">Bu eşikler program çalışırken dinamik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2b890-177">These thresholds are dynamically tuned as the program runs.</span></span>

  <span data-ttu-id="2b890-178">Bu tipik durumdur; çoğu GCs, yönetilen yığında ayırmalar nedeniyle gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="2b890-178">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="2b890-179"><xref:System.GC.Collect%2A?displayProperty=nameWithType>Yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2b890-179">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

  <span data-ttu-id="2b890-180">Parametresiz <xref:System.GC.Collect?displayProperty=nameWithType> yöntemi çağrılırsa veya başka bir aşırı yükleme <xref:System.GC.MaxGeneration?displayProperty=nameWithType> bir bağımsız değişken olarak GEÇIRILIYORSA Loh, yönetilen yığının geri kalanı ile birlikte toplanır.</span><span class="sxs-lookup"><span data-stu-id="2b890-180">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="2b890-181">Sistem düşük bellek durumunda.</span><span class="sxs-lookup"><span data-stu-id="2b890-181">The system is in low memory situation.</span></span>

  <span data-ttu-id="2b890-182">Bu durum, çöp toplayıcı IŞLETIM sisteminden yüksek bellek bildirimi aldığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="2b890-182">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="2b890-183">2. nesil GC 'yi yapan çöp toplayıcı 'nın üretken olması, bir tane tetikler.</span><span class="sxs-lookup"><span data-stu-id="2b890-183">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="2b890-184">LOH performansı etkileri</span><span class="sxs-lookup"><span data-stu-id="2b890-184">LOH performance implications</span></span>

<span data-ttu-id="2b890-185">Büyük nesne yığını üzerindeki ayırmaların performansı aşağıdaki yollarla etkiler.</span><span class="sxs-lookup"><span data-stu-id="2b890-185">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="2b890-186">Ayırma maliyeti.</span><span class="sxs-lookup"><span data-stu-id="2b890-186">Allocation cost.</span></span>

  <span data-ttu-id="2b890-187">CLR, verdiği her yeni nesne için belleğin temizlenme garantisi verir.</span><span class="sxs-lookup"><span data-stu-id="2b890-187">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="2b890-188">Bu, büyük bir nesnenin ayırma maliyetinin, bellek temizleme (bir GC tetiklediği durumlar dışında) tarafından tamamen eşit olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2b890-188">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="2b890-189">Bir bayt temizlemek için 2 döngü alırsa, en küçük büyük nesneyi temizlemek için 170.000 döngü sürer.</span><span class="sxs-lookup"><span data-stu-id="2b890-189">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="2b890-190">Bir 2GHz makinesindeki 16. nesnenin belleğinin temizlenmesi yaklaşık 16 MS sürer.</span><span class="sxs-lookup"><span data-stu-id="2b890-190">Clearing the memory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="2b890-191">Bu çok büyük bir maliyettir.</span><span class="sxs-lookup"><span data-stu-id="2b890-191">That's a rather large cost.</span></span>

- <span data-ttu-id="2b890-192">Toplama maliyeti.</span><span class="sxs-lookup"><span data-stu-id="2b890-192">Collection cost.</span></span>

  <span data-ttu-id="2b890-193">LOH ve 2. nesil birlikte toplandığından, birinin eşiği aşılırsa 2. nesil bir koleksiyon tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="2b890-193">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="2b890-194">2. nesil bir koleksiyon, LOH nedeniyle tetikleniyorsa 2. nesil GC 'den sonra çok daha küçük olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b890-194">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="2b890-195">2. nesil üzerinde çok fazla veri yoksa, bu en az etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2b890-195">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="2b890-196">Ancak 2. nesil büyükse, çok sayıda nesil 2 GB tetiklendiğinde performans sorunlarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-196">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="2b890-197">Birçok büyük nesne çok geçici olarak ayrılmışsa ve büyük bir SOH varsa, GCs 'yi çok fazla zaman harcamış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="2b890-197">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="2b890-198">Ayrıca, gerçekten büyük nesneleri ayırmayı ve bunlara izin vermek istiyorsanız ayırma maliyeti gerçekten eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-198">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="2b890-199">Başvuru türlerine sahip dizi öğeleri.</span><span class="sxs-lookup"><span data-stu-id="2b890-199">Array elements with reference types.</span></span>

  <span data-ttu-id="2b890-200">LOH üzerindeki çok büyük nesneler genellikle dizilerdir (gerçekten büyük bir örnek nesnesi olması çok nadir).</span><span class="sxs-lookup"><span data-stu-id="2b890-200">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="2b890-201">Bir dizinin öğeleri başvuru açısından zengin ise, öğeler referans açısından zengin değilse, mevcut olmayan bir maliyet doğurur.</span><span class="sxs-lookup"><span data-stu-id="2b890-201">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="2b890-202">Öğe herhangi bir başvuru içermiyorsa, çöp toplayıcının dizi içinde herhangi bir diziye gitmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2b890-202">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="2b890-203">Örneğin, düğümleri bir ikili ağaçta depolamak için bir dizi kullanırsanız, bunu uygulamanın bir yolu, bir düğümün sağ ve sol düğümüne gerçek düğümlere başvurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="2b890-203">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  <span data-ttu-id="2b890-204">`num_nodes`Büyükse, çöp toplayıcı her öğe için en az iki başvuruya gitmenize ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="2b890-204">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="2b890-205">Bir alternatif yaklaşım, sağ ve sol düğümlerin dizinini depooluşturmaktır:</span><span class="sxs-lookup"><span data-stu-id="2b890-205">An alternative approach is to store the index of the right and the left nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  <span data-ttu-id="2b890-206">Sol düğümün verilerini olarak `left.d` başvurmak yerine, buna olarak başvurabilirsiniz `binary_tr[left_index].d` .</span><span class="sxs-lookup"><span data-stu-id="2b890-206">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="2b890-207">Çöp toplayıcı 'nın sol ve sağ düğüm için herhangi bir başvuruya bakmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="2b890-207">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="2b890-208">Üç faktörden, ilk ikisi genellikle üçte daha önemdir.</span><span class="sxs-lookup"><span data-stu-id="2b890-208">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="2b890-209">Bu nedenle, geçici olanları ayırmak yerine yeniden kullandığınız büyük nesnelerin bir havuzunu ayırmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-209">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span>

## <a name="collect-performance-data-for-the-loh"></a><span data-ttu-id="2b890-210">LOH için performans verilerini toplama</span><span class="sxs-lookup"><span data-stu-id="2b890-210">Collect performance data for the LOH</span></span>

<span data-ttu-id="2b890-211">Belirli bir alan için performans verilerini toplamadan önce, aşağıdakileri yapmış olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="2b890-211">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="2b890-212">Bu alana baktığınız için kanıt bulundu.</span><span class="sxs-lookup"><span data-stu-id="2b890-212">Found evidence that you should be looking at this area.</span></span>

2. <span data-ttu-id="2b890-213">Gördüğünüz performans sorununu açıklayacak herhangi bir şeyi bulmaksızın, bildiğiniz diğer alanlardan haberdar olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b890-213">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="2b890-214">Bellek ve CPU temelleri hakkında daha fazla bilgi için [bir çözüm bulmaya çalışmadan önce blogda sorunu anlama](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2b890-214">See the blog [Understand the problem before you try to find a solution](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="2b890-215">LOH performansı üzerinde veri toplamak için aşağıdaki araçları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b890-215">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="2b890-216">.NET CLR bellek performansı sayaçları</span><span class="sxs-lookup"><span data-stu-id="2b890-216">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="2b890-217">ETW olayları</span><span class="sxs-lookup"><span data-stu-id="2b890-217">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="2b890-218">Bir hata ayıklayıcı</span><span class="sxs-lookup"><span data-stu-id="2b890-218">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="2b890-219">.NET CLR bellek performansı sayaçları</span><span class="sxs-lookup"><span data-stu-id="2b890-219">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="2b890-220">Bu performans sayaçları genellikle performans sorunlarını araştırmaya yönelik iyi bir ilk adımdır (ancak [ETW olaylarını](#etw-events)kullanmanızı öneririz).</span><span class="sxs-lookup"><span data-stu-id="2b890-220">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw-events)).</span></span> <span data-ttu-id="2b890-221">Şekil 4 ' ün gösterdiği gibi, istediğiniz sayaçları ekleyerek performans Izleyicisini yapılandırırsınız.</span><span class="sxs-lookup"><span data-stu-id="2b890-221">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="2b890-222">LOH ile ilgili olanlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2b890-222">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="2b890-223">**Gen 2 toplamaları**</span><span class="sxs-lookup"><span data-stu-id="2b890-223">**Gen 2 Collections**</span></span>

   <span data-ttu-id="2b890-224">İşlem başladıktan sonra 2. nesil oluşturma işleminin kaç kez gerçekleştiğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2b890-224">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="2b890-225">Sayaç, 2. kuşak koleksiyonun (tam çöp toplama da denir) sonunda artırılır.</span><span class="sxs-lookup"><span data-stu-id="2b890-225">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="2b890-226">Bu sayaç, son gözlemlenen değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2b890-226">This counter displays the last observed value.</span></span>

- <span data-ttu-id="2b890-227">**Büyük nesne yığın boyutu**</span><span class="sxs-lookup"><span data-stu-id="2b890-227">**Large Object Heap size**</span></span>

   <span data-ttu-id="2b890-228">LOH 'nin boş alanı da dahil olmak üzere geçerli boyutunu bayt cinsinden görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2b890-228">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="2b890-229">Bu sayaç her ayırmada değil çöp toplamanın sonunda güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-229">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="2b890-230">Performans sayaçlarından bakmak için yaygın olarak kullanılan bir yöntem, performans Izleyicisine (Perfmon. exe) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2b890-230">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="2b890-231">İlgilendiğiniz işlemlere yönelik ilginç sayaç eklemek için "Sayaç Ekle" öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2b890-231">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="2b890-232">Şekil 4 ' ün gösterdiği gibi, performans sayacı verilerini bir günlük dosyasına kaydedebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b890-232">You can save the performance counter data to a log file, as Figure 4 shows:</span></span>

<span data-ttu-id="2b890-233">![Performans sayaçlarını eklemeyi gösteren ekran görüntüsü.](media/large-object-heap/add-performance-counter.png)</span><span class="sxs-lookup"><span data-stu-id="2b890-233">![Screenshot that shows adding performance counters.](media/large-object-heap/add-performance-counter.png)</span></span>
<span data-ttu-id="2b890-234">Şekil 4:2. nesil GC sonrasında LOH</span><span class="sxs-lookup"><span data-stu-id="2b890-234">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="2b890-235">Performans sayaçları programlama yoluyla da sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-235">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="2b890-236">Birçok kişi bu şekilde rutin test sürecinin bir parçası olarak toplanır.</span><span class="sxs-lookup"><span data-stu-id="2b890-236">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="2b890-237">Sıradan olmayan değerlere sahip sayaçları fark ettikleri zaman, araştırmaya yardımcı olacak daha ayrıntılı veriler almak için başka bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b890-237">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="2b890-238">ETW çok daha zengin bilgi sağladığından performans sayaçları yerine ETW olaylarını kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="2b890-238">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw-events"></a><span data-ttu-id="2b890-239">ETW olayları</span><span class="sxs-lookup"><span data-stu-id="2b890-239">ETW events</span></span>

<span data-ttu-id="2b890-240">Çöp toplayıcı, yığının ne yaptığını ve nedenini anlamanıza yardımcı olmak için zengin bir ETW olayları kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b890-240">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="2b890-241">Aşağıdaki blog gönderileri ETW ile GC olaylarını nasıl toplayacağınızı ve anlayacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="2b890-241">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="2b890-242">GC ETW olayları-1</span><span class="sxs-lookup"><span data-stu-id="2b890-242">GC ETW Events - 1</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [<span data-ttu-id="2b890-243">GC ETW olayları-2</span><span class="sxs-lookup"><span data-stu-id="2b890-243">GC ETW Events - 2</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [<span data-ttu-id="2b890-244">GC ETW olayları-3</span><span class="sxs-lookup"><span data-stu-id="2b890-244">GC ETW Events - 3</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [<span data-ttu-id="2b890-245">GC ETW olayları-4</span><span class="sxs-lookup"><span data-stu-id="2b890-245">GC ETW Events - 4</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

<span data-ttu-id="2b890-246">Geçici LOH ayırmaları nedeniyle oluşan aşırı nesil 2 GB 'yi belirlemek için, GCs için tetikleyici nedeni sütununa bakın.</span><span class="sxs-lookup"><span data-stu-id="2b890-246">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="2b890-247">Yalnızca geçici büyük nesneleri ayıran basit bir test için aşağıdaki [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) komut SATıRı ile ETW olayları hakkında bilgi toplayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b890-247">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="2b890-248">Sonuç şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="2b890-248">The result is something like this:</span></span>

<span data-ttu-id="2b890-249">![PerfView 'da ETW olaylarını gösteren ekran görüntüsü.](media/large-object-heap/event-tracing-windows-perfview.png)</span><span class="sxs-lookup"><span data-stu-id="2b890-249">![Screenshot that shows ETW events in PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span></span>
<span data-ttu-id="2b890-250">Şekil 5: PerfView kullanılarak gösterilen ETW olayları</span><span class="sxs-lookup"><span data-stu-id="2b890-250">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="2b890-251">Görebileceğiniz gibi, tüm GCs 'ler 2 GB kuşak ve hepsi AllocLarge tarafından tetiklendikleri için, büyük bir nesnenin tahsis edilen bu GC 'yi tetiklediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2b890-251">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="2b890-252">**Loh kalan değer oranı%** sütunu %1 diyor olduğundan bu ayırmaların geçici olduğunu biliyoruz.</span><span class="sxs-lookup"><span data-stu-id="2b890-252">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="2b890-253">Bu büyük nesneleri kimin ayıryacağını söyleyen ek ETW olayları toplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b890-253">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="2b890-254">Aşağıdaki komut satırı:</span><span class="sxs-lookup"><span data-stu-id="2b890-254">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="2b890-255">ayırmaların yaklaşık olarak her 100.000 değerinde harekete geçen bir allocationtick olayı toplar.</span><span class="sxs-lookup"><span data-stu-id="2b890-255">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="2b890-256">Diğer bir deyişle, büyük bir nesne ayrıldığında her seferinde bir olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="2b890-256">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="2b890-257">Daha sonra, büyük nesneleri ayrılan çağrı yığınlarını gösteren GC yığın ayırma görünümlerinden birine bakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b890-257">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>

<span data-ttu-id="2b890-258">![Çöp toplayıcı yığın görünümünü gösteren ekran görüntüsü.](media/large-object-heap/garbage-collector-heap.png)</span><span class="sxs-lookup"><span data-stu-id="2b890-258">![Screenshot that shows a garbage collector heap view.](media/large-object-heap/garbage-collector-heap.png)</span></span>
<span data-ttu-id="2b890-259">Şekil 6: GC yığın ayırma görünümü</span><span class="sxs-lookup"><span data-stu-id="2b890-259">Figure 6: A GC Heap Alloc view</span></span>

<span data-ttu-id="2b890-260">Gördüğünüz gibi, bu çok basit bir sınamadır ve yalnızca kendi yönteminden büyük nesneleri ayırır `Main` .</span><span class="sxs-lookup"><span data-stu-id="2b890-260">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="2b890-261">Bir hata ayıklayıcı</span><span class="sxs-lookup"><span data-stu-id="2b890-261">A debugger</span></span>

<span data-ttu-id="2b890-262">Bir bellek dökümünlükleriniz varsa ve hangi nesnelerin gerçekten LOH üzerinde olduğuna bakmanız gerekiyorsa, .NET tarafından sunulan [sos hata ayıklayıcı uzantısını](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b890-262">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) provided by .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="2b890-263">Bu bölümde bahsedilen hata ayıklama komutları [Windows hata ayıklayıcıları](https://www.microsoft.com/whdc/devtools/debugging/default.mspx)için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2b890-263">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="2b890-264">Aşağıda, LOH 'yi analiz etmenin örnek çıktısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2b890-264">The following shows sample output from analyzing the LOH:</span></span>

```console
0:003> .loadby sos mscorwks
0:003> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013e35ec
sdgeneration 1 starts at 0x013e1b6c
generation 2 starts at 0x013e1000
ephemeral segment allocation context: none
segment   begin allocated     size
0018f2d0 790d5588 790f4b38 0x0001f5b0(128432)
013e0000 013e1000 013e35f8 0x000025f8(9720)
Large object heap starts at 0x023e1000
segment   begin allocated     size
023e0000 023e1000 033db630 0x00ffa630(16754224)
033e0000 033e1000 043cdf98 0x00fecf98(16699288)
043e0000 043e1000 05368b58 0x00f87b58(16284504)
Total Size 0x2f90cc8(49876168)
------------------------------
GC Heap Size 0x2f90cc8(49876168)
0:003> !dumpheap -stat 023e1000 033db630
total 133 objects
Statistics:
MT   Count   TotalSize Class Name
001521d0       66     2081792     Free
7912273c       63     6663696 System.Byte[]
7912254c       4     8008736 System.Object[]
Total 133 objects
```

<span data-ttu-id="2b890-265">LOH yığın boyutu (16.754.224 + 16.699.288 + 16.284.504) = 49.738.016 bayttır.</span><span class="sxs-lookup"><span data-stu-id="2b890-265">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="2b890-266">/Mm E1000 ve 033db630 adresleri arasında, 8.008.736 bayt bir nesne dizisi tarafından kullanılıyor <xref:System.Object?displayProperty=nameWithType> , 6.663.696 bayt bir nesne dizisi tarafından kullanılıyor <xref:System.Byte?displayProperty=nameWithType> ve 2.081.792 bayt boş alana göre yer kaplar.</span><span class="sxs-lookup"><span data-stu-id="2b890-266">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=nameWithType> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="2b890-267">Bazen hata ayıklayıcı, LOH 'nin toplam boyutunun 85.000 bayttan daha az olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b890-267">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="2b890-268">Bu durum, çalışma zamanının, büyük bir nesneden küçük bazı nesneleri ayırmak için LOH 'yi kullanması nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="2b890-268">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="2b890-269">LOH sıkıştırmadığından, bazen LOH 'nin parçalanma kaynağı olduğu düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="2b890-269">Because the LOH is not compacted, sometimes the LOH is thought to be the source of fragmentation.</span></span> <span data-ttu-id="2b890-270">Parçalanma anlamı:</span><span class="sxs-lookup"><span data-stu-id="2b890-270">Fragmentation means:</span></span>

- <span data-ttu-id="2b890-271">Yönetilen yığının, yönetilen nesneler arasındaki boş alan miktarına göre belirtilen parçalanması.</span><span class="sxs-lookup"><span data-stu-id="2b890-271">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="2b890-272">SoS 'de, `!dumpheap –type Free` komut yönetilen nesneler arasındaki boş alan miktarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2b890-272">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="2b890-273">Olarak işaretlenen bellek olan sanal bellek (VM) adres alanının parçalanması `MEM_FREE` .</span><span class="sxs-lookup"><span data-stu-id="2b890-273">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="2b890-274">WinDbg 'de çeşitli hata ayıklayıcı komutlarını kullanarak edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b890-274">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="2b890-275">Aşağıdaki örnek, VM alanındaki parçalanmayı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="2b890-275">The following example shows fragmentation in the VM space:</span></span>

   ```console
   0:000> !address
   00000000 : 00000000 - 00010000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   00010000 : 00010000 - 00002000
   Type     00020000 MEM_PRIVATE
   Protect 00000004 PAGE_READWRITE
   State   00001000 MEM_COMMIT
   Usage   RegionUsageEnvironmentBlock
   00012000 : 00012000 - 0000e000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   … [omitted]
   -------------------- Usage SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Pct(Busy)   Usage
   701000 (   7172) : 00.34%   20.69%   : RegionUsageIsVAD
   7de15000 ( 2062420) : 98.35%   00.00%   : RegionUsageFree
   1452000 (   20808) : 00.99%   60.02%   : RegionUsageImage
   300000 (   3072) : 00.15%   08.86%   : RegionUsageStack
   3000 (     12) : 00.00%   00.03%   : RegionUsageTeb
   381000 (   3588) : 00.17%   10.35%   : RegionUsageHeap
   0 (       0) : 00.00%   00.00%   : RegionUsagePageHeap
   1000 (       4) : 00.00%   00.01%   : RegionUsagePeb
   1000 (       4) : 00.00%   00.01%   : RegionUsageProcessParametrs
   2000 (       8) : 00.00%   00.02%   : RegionUsageEnvironmentBlock
   Tot: 7fff0000 (2097088 KB) Busy: 021db000 (34668 KB)

   -------------------- Type SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   7de15000 ( 2062420) : 98.35%   : <free>
   1452000 (   20808) : 00.99%   : MEM_IMAGE
   69f000 (   6780) : 00.32%   : MEM_MAPPED
   6ea000 (   7080) : 00.34%   : MEM_PRIVATE

   -------------------- State SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   1a58000 (   26976) : 01.29%   : MEM_COMMIT
   7de15000 ( 2062420) : 98.35%   : MEM_FREE
   783000 (   7692) : 00.37%   : MEM_RESERVE

   Largest free region: Base 01432000 - Size 707ee000 (1843128 KB)
   ```

<span data-ttu-id="2b890-276">Atık toplayıcısının genellikle IŞLETIM sisteminden yeni yönetilen yığın kesimleri elde etmek ve yeniden işletim sistemine tekrar serbest bırakmak için çöp toplayıcı 'nın neden olduğu geçici büyük nesnelerden kaynaklanan VM parçalanması ' nı görmek daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="2b890-276">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="2b890-277">LOH 'nin VM [parçalanmaya](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) neden olup olmadığını doğrulamak Için, [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) üzerinde bir kesme noktası ayarlayabilir ve onları kimlerin çağırabildiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b890-277">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) and [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) to see who call them.</span></span> <span data-ttu-id="2b890-278">Örneğin, IŞLETIM sisteminden 8MBB 'den büyük sanal bellek öbekleri ayırmaya çalışan kişileri görmek için şöyle bir kesme noktası ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b890-278">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="2b890-279">Bu komut, hata ayıklayıcıya kesilir ve çağrı yığınını yalnızca, [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) 'tan daha büyük bir ayırma boyutuyla (0x800000) çağrıldığında çağrı yığınını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b890-279">This command breaks into the debugger and shows the call stack only if [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="2b890-280">CLR 2,0, parçaların (büyük ve küçük nesne yığınlarıyla birlikte) sıklıkla alındığı ve yayımlandığı senaryolar için yararlı olabilecek *VM hoarding* adlı bir özellik ekledi.</span><span class="sxs-lookup"><span data-stu-id="2b890-280">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarios where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="2b890-281">VM hoarding belirtmek için `STARTUP_HOARD_GC_VM` barındırma API 'si aracılığıyla çağrılan bir başlangıç bayrağı belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b890-281">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="2b890-282">CLR, boş kesimleri yeniden işletim sistemine serbest bırakmak yerine bu kesimlerdeki belleği kaydeder ve bir bekleme listesine koyar.</span><span class="sxs-lookup"><span data-stu-id="2b890-282">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="2b890-283">(CLR 'nin bunu çok büyük kesimler için yapamadığını unutmayın.) CLR daha sonra yeni segment isteklerini karşılamak için bu segmentleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b890-283">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="2b890-284">Uygulamanız yeni bir kesime bir dahaki sefer ihtiyaç duyduğunda, CLR, yeterince büyük bir bulması durumunda bu bekleme listesinden bir tane kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b890-284">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="2b890-285">VM hoarding, bellek dışı özel durumların önüne geçmek için, sistemde çalışan baskın uygulamalar gibi bazı sunucu uygulamaları gibi zaten elde ettikleri kesimlerde tutmak isteyen uygulamalar için de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="2b890-285">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out-of-memory exceptions.</span></span>

<span data-ttu-id="2b890-286">Uygulamanızın oldukça kararlı bellek kullanımına sahip olduğundan emin olmak için bu özelliği kullandığınızda uygulamanızı dikkatle test etmenizi kesinlikle öneririz.</span><span class="sxs-lookup"><span data-stu-id="2b890-286">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>
