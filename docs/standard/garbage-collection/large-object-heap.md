---
title: Windows'da LOH - .NET
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: 5125b76dd26ffa4fb363ecf8449f65b490f57b93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74283615"
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="3d8f8-102">Windows sistemlerinde büyük nesne yığını</span><span class="sxs-lookup"><span data-stu-id="3d8f8-102">The large object heap on Windows systems</span></span>

<span data-ttu-id="3d8f8-103">.NET Çöp Toplayıcı (GC) nesneleri küçük ve büyük nesnelere böler.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-103">The .NET Garbage Collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="3d8f8-104">Bir nesne büyükolduğunda, bazı öznitelikleri nesne küçükse daha önemli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-104">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="3d8f8-105">Örneğin, sıkıştırmak -- yani yığının başka bir yerinde hafızaya kopyalamak -- pahalıya mal olabilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-105">For instance, compacting it -- that is, copying it in memory elsewhere on the heap -- can be expensive.</span></span> <span data-ttu-id="3d8f8-106">Bu nedenle, .NET Çöp Toplayıcı büyük nesne yığını (LOH) üzerinde büyük nesneler yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-106">Because of this, the .NET Garbage Collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="3d8f8-107">Bu konuda, büyük nesne yığınına derinlemesine bakacağız.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-107">In this topic, we'll look at the large object heap in depth.</span></span> <span data-ttu-id="3d8f8-108">Bir nesneyi büyük bir nesne olarak nitelemeyi, bu büyük nesnelerin nasıl toplandığını ve büyük nesnelerin ne tür performans etkileri uyguladığını tartışacağız.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-108">We'll discuss what qualifies an object as a large object, how these large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d8f8-109">Bu konu, .NET Framework ve .NET Core'da yalnızca Windows sistemlerinde çalışan büyük nesne yığınını tartışır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-109">This topic discusses the large object heap in the .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="3d8f8-110">Diğer platformlarda .NET uygulamalarında çalışan LOH'yu kapsamaz.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-110">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a><span data-ttu-id="3d8f8-111">Bir nesnenin büyük nesne yığınına nasıl son verdiği ve GC'nin bunları nasıl işlediği</span><span class="sxs-lookup"><span data-stu-id="3d8f8-111">How an object ends up on the large object heap and how GC handles them</span></span>

<span data-ttu-id="3d8f8-112">Bir nesne 85.000 bayt boyutundan büyük veya eşitse, büyük bir nesne olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-112">If an object is greater than or equal to 85,000 bytes in size, it’s considered a large object.</span></span> <span data-ttu-id="3d8f8-113">Bu sayı performans amıile belirlendi.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-113">This number was determined by performance tuning.</span></span> <span data-ttu-id="3d8f8-114">Bir nesne ayırma isteği 85.000 veya daha fazla bayt için olduğunda, çalışma zamanı onu büyük nesne yığınına ayırır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-114">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="3d8f8-115">Bunun ne anlama geldiğini anlamak için .NET GC ile ilgili bazı temel leri incelemek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-115">To understand what this means, it's useful to examine some fundamentals about the .NET GC.</span></span>

<span data-ttu-id="3d8f8-116">.NET Çöp Toplayıcı bir nesil toplayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-116">The .NET Garbage Collector is a generational collector.</span></span> <span data-ttu-id="3d8f8-117">Üç kuşağı vardır: nesil 0, nesil 1 ve nesil 2.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-117">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="3d8f8-118">3 nesil olmasının nedeni, iyi ayarlanmış bir uygulamada, çoğu nesnenin gen0'de ölmesidir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-118">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="3d8f8-119">Örneğin, bir sunucu uygulamasında, her istekle ilişkili ayırmalar istek tamamlandıktan sonra ölür.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-119">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="3d8f8-120">Uçuş tahsis talepleri gen1'e dönüşecek ve orada ölecek.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-120">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="3d8f8-121">Esasen, gen1 genç nesne alanları ve uzun ömürlü nesne alanları arasında bir tampon görevi görür.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-121">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="3d8f8-122">Küçük nesneler her zaman nesil 0'da ayrılır ve kullanım ömürlerine bağlı olarak nesil 1 veya nesil2'ye yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-122">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="3d8f8-123">Büyük nesneler her zaman nesil 2'de ayrılır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-123">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="3d8f8-124">Büyük nesneler nesil 2'ye aittir, çünkü yalnızca nesil 2 koleksiyonu sırasında toplanır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-124">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="3d8f8-125">Bir nesil toplandığında, tüm genç nesil (ler) de toplanır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-125">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="3d8f8-126">Örneğin, bir nesil 1 GC gerçekleştiğinde, hem nesil 1 hem de 0 toplanır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-126">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="3d8f8-127">Ve bir nesil 2 GC olduğunda, tüm yığın toplanır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-127">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="3d8f8-128">Bu nedenle, bir nesil 2 GC de *tam GC*denir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-128">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="3d8f8-129">Bu makalede, tam GC yerine nesil 2 GC anlamına gelir, ancak terimler değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-129">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="3d8f8-130">Nesiller GC yığınının mantıksal bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-130">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="3d8f8-131">Fiziksel olarak, nesneler yönetilen yığın segmentlerde yaşar.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-131">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="3d8f8-132">*Yönetilen yığın kesimi,* Yönetilen kod adına [VirtualAlloc işlevini](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) arayarak GC'nin işletim sistemi tarafından rezerve ettiği bir bellek yığınıdır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-132">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) on behalf of managed code.</span></span> <span data-ttu-id="3d8f8-133">CLR yüklendiğinde, GC iki başlangıç yığını ayırır: biri küçük nesneler (küçük nesne yığını veya SOH) ve biri büyük nesneler (büyük nesne yığını) için.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-133">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the small object heap, or SOH), and one for large objects (the large object heap).</span></span>

<span data-ttu-id="3d8f8-134">Ayırma istekleri daha sonra yönetilen nesneleri bu yönetilen yığın kesimlerine koyarak karşılanır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-134">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="3d8f8-135">Nesne 85.000 bayttan azsa, SOH için segmente konur; aksi takdirde, bir LOH segmenti üzerine konur.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-135">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="3d8f8-136">Daha fazla nesne onlara ayrıldıkça, segmentler (daha küçük parçalar halinde) işlenir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-136">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="3d8f8-137">SOH için, bir GC hayatta nesneler sonraki nesile yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-137">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="3d8f8-138">Bir nesil 0 koleksiyonu hayatta nesneler artık nesil 1 nesneleri olarak kabul edilir, ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-138">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="3d8f8-139">Ancak, en eski nesil hayatta nesneler hala en eski nesil olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-139">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="3d8f8-140">Başka bir deyişle, nesil 2'den hayatta kalanlar nesil 2 nesneleridir; ve LOH kurtulanların LOH nesneleri (gen2 ile toplanır).</span><span class="sxs-lookup"><span data-stu-id="3d8f8-140">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span>

<span data-ttu-id="3d8f8-141">Kullanıcı kodu yalnızca nesil 0 (küçük nesneler) veya LOH (büyük nesneler) olarak tahsis edilebilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-141">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="3d8f8-142">Sadece GC, nesil 1'deki nesneleri (nesil 0'dan kurtulanları teşvik ederek) ve nesil 2'de (1 ve 2. nesilden kurtulanları teşvik ederek) "tahsis edebilir".</span><span class="sxs-lookup"><span data-stu-id="3d8f8-142">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="3d8f8-143">Bir çöp toplama tetiklendiğinde, GC canlı nesneleri izler ve sıkıştırılır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-143">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="3d8f8-144">Ama sıkıştırma pahalı olduğu için, GC LOH *süpürür;* daha sonra büyük nesne ayırma isteklerini karşılamak için yeniden kullanılabilecek ölü nesnelerden ücretsiz bir liste yapar.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-144">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="3d8f8-145">Bitişik ölü nesneler tek bir boş nesne haline getirilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-145">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="3d8f8-146">.NET Core ve .NET Framework (.NET Framework 4.5.1 ile başlayarak) kullanıcıların bir sonraki tam engelleme GC sırasında LOH sıkıştırılmış olması gerektiğini belirtmelerini sağlayan <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-146">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="3d8f8-147">Ve gelecekte, .NET Otomatik olarak LOH sıkıştırmaya karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-147">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="3d8f8-148">Bu, büyük nesneleri ayırDığınız ve hareket etmediklerinden emin olmak istiyorsanız, yine de sabitlemeniz gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-148">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="3d8f8-149">Şekil 1, GC'nin ilk nesil 0 GC'den `Obj1` sonra `Obj3` nesil 1'i oluşturduğu ve nerede ve ölü `Obj2` `Obj5` olduğu ilk nesil 1 GC'den sonra nesil 2'yi oluşturduğu bir senaryoyu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-149">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="3d8f8-150">Bu ve aşağıdaki şekillerin yalnızca illüstrasyon amaçlı olduğunu unutmayın; yığında ne olduğunu daha iyi göstermek için çok az nesne içerirler.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-150">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="3d8f8-151">Gerçekte, çok daha fazla nesne genellikle bir GC yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-151">In reality, many more objects are typically involved in a GC.</span></span>

![Şekil 1: Bir gen 0 GC ve bir gen 1 GC](media/loh/loh-figure-1.jpg)\
<span data-ttu-id="3d8f8-153">Şekil 1: Bir nesil 0 ve bir nesil 1 GC.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-153">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="3d8f8-154">Şekil 2 bir nesil sonra gösterir 2 `Obj1` `Obj2` GC bu gördüm ve ölü, GC tarafından işgal edildi `Obj1` ve `Obj2`daha sonra bir tahsis isteği karşılamak `Obj4`için kullanılan bellek bitişik boş alan oluşturur .</span><span class="sxs-lookup"><span data-stu-id="3d8f8-154">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="3d8f8-155">Son nesneden sonraki `Obj3`boşluk, segmentin sonuna kadar ayırma isteklerini karşılamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-155">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>

![Şekil 2: Bir gen 2 GC sonra](media/loh/loh-figure-2.jpg)\
<span data-ttu-id="3d8f8-157">Şekil 2: Bir nesil sonra 2 GC</span><span class="sxs-lookup"><span data-stu-id="3d8f8-157">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="3d8f8-158">Büyük nesne ayırma isteklerini karşılamak için yeterli boş alan yoksa, GC önce işletim sistemi'nden daha fazla segment elde etmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-158">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="3d8f8-159">Bu başarısız olursa, bir nesil tetikler 2 GC biraz yer boşaltma umuduyla.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-159">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="3d8f8-160">Bir nesil 1 veya nesil 2 GC sırasında, çöp toplayıcı [VirtualFree işlevini](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree)çağırarak işletim sistemi geri üzerinde hiçbir canlı nesne var segmentleri bültenleri.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-160">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span></span> <span data-ttu-id="3d8f8-161">Segmentin sonuna kadar ki son canlı nesneden sonraki boşluk ayrılır (gen0/gen1'in yaşadığı geçici segment dışında, çöp toplayıcının bazı larını bağlı tuttuğu, çünkü uygulamanız hemen içinde tahsis edilecektir).</span><span class="sxs-lookup"><span data-stu-id="3d8f8-161">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="3d8f8-162">Ve boş alanlar sıfırlanır, yani işletim sistemi diske geri veri yazmak gerekmez kararlı kalır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-162">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="3d8f8-163">LOH sadece nesil 2 GCs sırasında toplanır yana, LOH segmenti sadece böyle bir GC sırasında serbest bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-163">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="3d8f8-164">Şekil 3, çöp toplayıcının bir kesimi (segment 2) işletim sistemi için geri saldığı ve kalan segmentlerde daha fazla alan ayırdığı bir senaryoyu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-164">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="3d8f8-165">Büyük nesne ayırma isteklerini karşılamak için kesimin sonundaki adanmış alanı kullanması gerekiyorsa, belleği yeniden işler.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-165">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="3d8f8-166">(Commit/decommit bir açıklama için, [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc)için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-166">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span></span>

![Şekil 3: LOH sonra bir gen 2 GC](media/loh/loh-figure-3.jpg)\
<span data-ttu-id="3d8f8-168">Şekil 3: Bir nesil 2 GC sonra LOH</span><span class="sxs-lookup"><span data-stu-id="3d8f8-168">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="3d8f8-169">Büyük bir nesne ne zaman toplanır?</span><span class="sxs-lookup"><span data-stu-id="3d8f8-169">When is a large object collected?</span></span>

<span data-ttu-id="3d8f8-170">Genel olarak, aşağıdaki 3 koşuldan biri gerçekleştiğinde bir GC oluşur:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-170">In general, a GC occurs when one of the following 3 conditions happens:</span></span>

- <span data-ttu-id="3d8f8-171">Ayırma, nesil 0 veya büyük nesne eşiğini aşıyor.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-171">Allocation exceeds the generation 0 or large object threshold.</span></span>

  <span data-ttu-id="3d8f8-172">Eşik bir neslin özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-172">The threshold is a property of a generation.</span></span> <span data-ttu-id="3d8f8-173">Çöp toplayıcı nesneleri içine ayırdığında bir nesil için bir eşik ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-173">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="3d8f8-174">Eşik aşıldığında, o nesilde bir GC tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-174">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="3d8f8-175">Küçük veya büyük nesneleri ayırdığınızda, sırasıyla nesil 0 ve LOH eşiklerini tüketirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-175">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="3d8f8-176">Çöp toplayıcısı nesil 1 ve 2'ye ayrıldıklarında, eşiklerini tüketir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-176">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="3d8f8-177">Program çalışırken bu eşikler dinamik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-177">These thresholds are dynamically tuned as the program runs.</span></span>

  <span data-ttu-id="3d8f8-178">Bu tipik bir durumdur; çoğu GC, yönetilen yığındaki ayırmalar nedeniyle gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-178">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="3d8f8-179">Yöntem <xref:System.GC.Collect%2A?displayProperty=nameWithType> denir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-179">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

  <span data-ttu-id="3d8f8-180">Parametresiz <xref:System.GC.Collect?displayProperty=nameWithType> yöntem çağrılır veya başka <xref:System.GC.MaxGeneration?displayProperty=nameWithType> bir aşırı yük bir bağımsız değişken olarak geçirilirse, LOH yönetilen yığının geri kalanı ile birlikte toplanır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-180">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="3d8f8-181">Sistem düşük bellek durumunda.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-181">The system is in low memory situation.</span></span>

  <span data-ttu-id="3d8f8-182">Bu, çöp toplayıcı işletim sistemi yüksek bellek bildirimi aldığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-182">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="3d8f8-183">Çöp toplayıcı bir nesil 2 GC yapmanın verimli olacağını düşünüyorsa, bir tetikler.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-183">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="3d8f8-184">LOH Performans Etkileri</span><span class="sxs-lookup"><span data-stu-id="3d8f8-184">LOH Performance Implications</span></span>

<span data-ttu-id="3d8f8-185">Büyük nesne yığınıüzerindeki ayırmalar performansı aşağıdaki şekillerde etkiler.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-185">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="3d8f8-186">Tahsis maliyeti.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-186">Allocation cost.</span></span>

  <span data-ttu-id="3d8f8-187">CLR, verdiği her yeni nesnenin belleği temizlenir garantisi verir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-187">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="3d8f8-188">Bu, büyük bir nesnenin ayırma maliyetinin bellek temizleme tarafından tamamen baskın olduğu anlamına gelir (gc tetiklemediği sürece).</span><span class="sxs-lookup"><span data-stu-id="3d8f8-188">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="3d8f8-189">Bir bayttemizlemek için 2 döngü gerekiyorsa, en küçük büyük nesneyi temizlemek için 170.000 döngü alır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-189">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="3d8f8-190">2GHz makinedeki 16MB'lık bir nesnenin belleği temizlemek yaklaşık 16 m sürer.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-190">Clearing the memory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="3d8f8-191">Bu oldukça büyük bir bedel.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-191">That's a rather large cost.</span></span>

- <span data-ttu-id="3d8f8-192">Tahsilat maliyeti.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-192">Collection cost.</span></span>

  <span data-ttu-id="3d8f8-193">LOH ve nesil 2 birlikte toplandığı için, birinin eşiği aşılırsa, bir nesil 2 koleksiyonu tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-193">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="3d8f8-194">LOH nedeniyle bir nesil 2 koleksiyonu tetiklenirse, nesil 2 mutlaka GC sonra çok daha küçük olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-194">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="3d8f8-195">Nesil 2 hakkında çok fazla veri yoksa, bu en az etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-195">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="3d8f8-196">Ancak nesil 2 büyükse, birçok nesil 2 GC tetiklenirse performans sorunlarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-196">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="3d8f8-197">Birçok büyük nesneler çok geçici olarak tahsis edilir ve büyük bir SOH varsa, GCs yaparken çok fazla zaman harcama olabilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-197">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="3d8f8-198">Buna ek olarak, gerçekten büyük nesneleri ayırmaya ve bırakmaya devam ederseniz, tahsis maliyeti gerçekten ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-198">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="3d8f8-199">Başvuru türlerine sahip dizi öğeleri.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-199">Array elements with reference types.</span></span>

  <span data-ttu-id="3d8f8-200">LOH üzerinde çok büyük nesneler genellikle diziler (gerçekten büyük bir örnek nesne olması çok nadirdir).</span><span class="sxs-lookup"><span data-stu-id="3d8f8-200">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="3d8f8-201">Bir dizinin öğeleri referans açısından zenginse, öğeler referans açısından zengin değilse, bulunmayan bir maliyete neden olur.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-201">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="3d8f8-202">Öğe herhangi bir başvuru içermiyorsa, çöp toplayıcının diziden geçmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-202">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="3d8f8-203">Örneğin, düğümleri ikili bir ağaçta depolamak için bir dizi kullanıyorsanız, bunu uygulamanın bir yolu, bir düğümün sağ ve sol düğümüne gerçek düğümler tarafından başvurmaktır:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-203">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  <span data-ttu-id="3d8f8-204">`num_nodes` Büyükse, çöp toplayıcının öğe başına en az iki başvurudan geçmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-204">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="3d8f8-205">Alternatif bir yaklaşım, sağ ve sol düğümdizisini depolamaktır:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-205">An alternative approach is to store the index of the right and the left nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  <span data-ttu-id="3d8f8-206">Sol düğümün verilerini " olarak `left.d` `binary_tr[left_index].d`adlandırmak yerine.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-206">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="3d8f8-207">Ve çöp toplayıcı sol ve sağ düğüm için herhangi bir referans bakmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-207">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="3d8f8-208">Üç faktörden, ilk ikisi genellikle üçüncüfaktörden daha önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-208">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="3d8f8-209">Bu nedenle, geçici nesneler ayırmak yerine yeniden kullandığınız büyük nesnelerden oluşan bir havuz ayırmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-209">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span>

## <a name="collecting-performance-data-for-the-loh"></a><span data-ttu-id="3d8f8-210">LOH için performans verileri toplama</span><span class="sxs-lookup"><span data-stu-id="3d8f8-210">Collecting performance data for the LOH</span></span>

<span data-ttu-id="3d8f8-211">Belirli bir alan için performans verileri toplamadan önce aşağıdakileri zaten yapmış olmalısınız:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-211">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="3d8f8-212">Bu bölgeye bakmanız gerektiğine dair kanıt buldum.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-212">Found evidence that you should be looking at this area.</span></span>

2. <span data-ttu-id="3d8f8-213">Gördüğünüz performans sorununu açıklayabilecek hiçbir şey bulamadan bildiğiniz diğer alanları tükettiniz.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-213">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="3d8f8-214">Bloga bakın Bellek ve CPU temelleri hakkında daha fazla bilgi için [bir çözüm bulmaya çalışmadan önce sorunu anlayın.](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/)</span><span class="sxs-lookup"><span data-stu-id="3d8f8-214">See the blog [Understand the problem before you try to find a solution](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="3d8f8-215">LOH performansı hakkında veri toplamak için aşağıdaki araçları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-215">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="3d8f8-216">.NET CLR bellek performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="3d8f8-216">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="3d8f8-217">ETW olayları</span><span class="sxs-lookup"><span data-stu-id="3d8f8-217">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="3d8f8-218">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="3d8f8-218">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="3d8f8-219">.NET CLR Bellek Performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="3d8f8-219">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="3d8f8-220">Bu performans sayaçları genellikle performans sorunlarını araştırmak için iyi bir ilk adımdır [(etw olaylarını](#etw-events)kullanmanızı öneririmıza rağmen).</span><span class="sxs-lookup"><span data-stu-id="3d8f8-220">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw-events)).</span></span> <span data-ttu-id="3d8f8-221">Şekil 4'ün gösterdiği gibi, istediğiniz sayaçları ekleyerek Performans Monitörü'ne yapılandırırsınız.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-221">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="3d8f8-222">LOH ile ilgili olanlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-222">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="3d8f8-223">**Gen 2 Koleksiyonları**</span><span class="sxs-lookup"><span data-stu-id="3d8f8-223">**Gen 2 Collections**</span></span>

   <span data-ttu-id="3d8f8-224">İşlemin başlamasından bu yana nesil 2 GC'lerin oluşma sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-224">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="3d8f8-225">Sayaç, bir nesil 2 koleksiyonunun sonunda (tam çöp toplama olarak da adlandırılır) artıyla şıvlanır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-225">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="3d8f8-226">Bu sayaç, gözlenen son değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-226">This counter displays the last observed value.</span></span>

- <span data-ttu-id="3d8f8-227">**Büyük Nesne Yığını boyutu**</span><span class="sxs-lookup"><span data-stu-id="3d8f8-227">**Large Object Heap size**</span></span>

   <span data-ttu-id="3d8f8-228">LOH'un boş alan da dahil olmak üzere geçerli boyutunu baytlar halinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-228">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="3d8f8-229">Bu sayaç, her ayırmada değil, çöp toplamanın sonunda güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-229">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="3d8f8-230">Performans sayaçlarına bakmanın yaygın bir yolu Performance Monitor (perfmon.exe) iledir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-230">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="3d8f8-231">Önemsediğiniz işlemler için ilginç sayacı eklemek için "Sayaç Ekle"yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-231">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="3d8f8-232">Şekil 4'ün gösterdiği gibi performans sayacı verilerini bir günlük dosyasına kaydedebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-232">You can save the performance counter data to a log file, as Figure 4 shows:</span></span>

<span data-ttu-id="3d8f8-233">![Performans sayaçları eklemeyi gösteren ekran görüntüsü.](media/large-object-heap/add-performance-counter.png)</span><span class="sxs-lookup"><span data-stu-id="3d8f8-233">![Screenshot that shows adding performance counters.](media/large-object-heap/add-performance-counter.png)</span></span>
<span data-ttu-id="3d8f8-234">Şekil 4: Bir nesil 2 GC sonra LOH</span><span class="sxs-lookup"><span data-stu-id="3d8f8-234">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="3d8f8-235">Performans sayaçları da programlı olarak sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-235">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="3d8f8-236">Birçok kişi rutin test sürecinin bir parçası olarak bu şekilde toplamak.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-236">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="3d8f8-237">Sıra dışı değerlere sahip sayaçları tespit ettiklerinde, soruşturmaya yardımcı olmak için daha ayrıntılı veriler elde etmek için başka araçlar kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-237">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="3d8f8-238">ETW çok daha zengin bilgiler sağladığından, performans sayaçları yerine ETW etkinliklerini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-238">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw-events"></a><span data-ttu-id="3d8f8-239">ETW olayları</span><span class="sxs-lookup"><span data-stu-id="3d8f8-239">ETW events</span></span>

<span data-ttu-id="3d8f8-240">Çöp toplayıcı, yığının ne yaptığını ve neden yaptığını anlamanıza yardımcı olmak için zengin bir ETW olayı kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-240">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="3d8f8-241">Aşağıdaki blog gönderileri, ETW ile GC etkinliklerinin nasıl toplandığını ve anlayacağımı gösterir:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-241">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="3d8f8-242">GC ETW Etkinlikleri - 1</span><span class="sxs-lookup"><span data-stu-id="3d8f8-242">GC ETW Events - 1</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [<span data-ttu-id="3d8f8-243">GC ETW Etkinlikleri - 2</span><span class="sxs-lookup"><span data-stu-id="3d8f8-243">GC ETW Events - 2</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [<span data-ttu-id="3d8f8-244">GC ETW Etkinlikleri - 3</span><span class="sxs-lookup"><span data-stu-id="3d8f8-244">GC ETW Events - 3</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [<span data-ttu-id="3d8f8-245">GC ETW Etkinlikleri - 4</span><span class="sxs-lookup"><span data-stu-id="3d8f8-245">GC ETW Events - 4</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

<span data-ttu-id="3d8f8-246">Geçici LOH ayırmalarının neden olduğu aşırı nesil 2 GC'leri tanımlamak için, GC'ler için Tetikleme Nedeni sütununa bakın.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-246">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="3d8f8-247">Yalnızca geçici büyük nesneler ayıran basit bir sınama için, aşağıdaki [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) komut satırıyla ETW olayları hakkında bilgi toplayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-247">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="3d8f8-248">Sonuç şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-248">The result is something like this:</span></span>

<span data-ttu-id="3d8f8-249">![PerfView'deki ETW olaylarını gösteren ekran görüntüsü.](media/large-object-heap/event-tracing-windows-perfview.png)</span><span class="sxs-lookup"><span data-stu-id="3d8f8-249">![Screenshot that shows ETW events in PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span></span>
<span data-ttu-id="3d8f8-250">Şekil 5: PerfView kullanılarak gösterilen ETW olayları</span><span class="sxs-lookup"><span data-stu-id="3d8f8-250">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="3d8f8-251">Gördüğünüz gibi, tüm GC'ler nesil 2 GC'lerdir ve hepsi AllocLarge tarafından tetiklenir, bu da büyük bir nesnenin ayrılmasının bu GC'yi tetiklediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-251">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="3d8f8-252">**LOH Survival Rate %** sütununda %1 yazdığı için bu ayırmaların geçici olduğunu biliyoruz.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-252">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="3d8f8-253">Bu büyük nesneleri kimin ayırdığını söyleyen ek ETW olayları toplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-253">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="3d8f8-254">Aşağıdaki komut satırı:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-254">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="3d8f8-255">yaklaşık her 100k değerindeki tahsisatları ateşleyen bir TahsisatTick olayı toplar.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-255">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="3d8f8-256">Başka bir deyişle, büyük bir nesne her tahsis edide bir olay ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-256">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="3d8f8-257">Daha sonra, büyük nesneleri ayıran çağrı yığınlarını gösteren GC Heap Alloc görünümlerinden birine bakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-257">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>

<span data-ttu-id="3d8f8-258">![Çöp toplayıcı yığını görünümünü gösteren ekran görüntüsü.](media/large-object-heap/garbage-collector-heap.png)</span><span class="sxs-lookup"><span data-stu-id="3d8f8-258">![Screenshot that shows a garbage collector heap view.](media/large-object-heap/garbage-collector-heap.png)</span></span>
<span data-ttu-id="3d8f8-259">Şekil 6: Bir GC Yığın Alloc görünümü</span><span class="sxs-lookup"><span data-stu-id="3d8f8-259">Figure 6: A GC Heap Alloc view</span></span>

<span data-ttu-id="3d8f8-260">Gördüğünüz gibi, bu sadece `Main` kendi yönteminden büyük nesneleri ayıran çok basit bir testtir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-260">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="3d8f8-261">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="3d8f8-261">A debugger</span></span>

<span data-ttu-id="3d8f8-262">Sahip olduğunuz tek şey bir bellek dökümüyse ve LOH'da gerçekte hangi nesnelere sahip seniz, .NET tarafından sağlanan [SoS hata ayıklama uzantısını](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-262">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) provided by .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="3d8f8-263">Bu bölümde belirtilen hata ayıklama komutları Windows [Hata Ayıklayıcıları](https://www.microsoft.com/whdc/devtools/debugging/default.mspx)için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-263">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="3d8f8-264">Aşağıdaki LOH analiz örnek çıktı gösterir:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-264">The following shows sample output from analyzing the LOH:</span></span>

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

<span data-ttu-id="3d8f8-265">LOH yığın boyutu (16.754.224 + 16.699.288 + 16.284.504) = 49.738.016 bayt.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-265">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="3d8f8-266">023e1000 ve 033db630 adresleri arasında, 8.008.736 bayt <xref:System.Object?displayProperty=nameWithType> bir dizi nesne tarafından işgal edilir, 6.663.696 bayt <xref:System.Byte?displayProperty=nameWithType> nesnelerin bir dizi tarafından işgal edilir ve 2.081.792 bayt boş alan tarafından işgal edilir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-266">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=nameWithType> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="3d8f8-267">Bazen hata ayıklama, LOH'un toplam boyutunun 85.000 bayttan az olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-267">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="3d8f8-268">Çalışma zamanının kendisi büyük bir nesneden daha küçük bazı nesneleri ayırmak için LOH'yu kullandığından bu durumda olur.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-268">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="3d8f8-269">LOH sıkıştırılmış olmadığından, bazen LOH parçalanma kaynağı olduğu düşünülmektedir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-269">Because the LOH is not compacted, sometimes the LOH is thought to be the source of fragmentation.</span></span> <span data-ttu-id="3d8f8-270">Parçalanma nın anlamı:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-270">Fragmentation means:</span></span>

- <span data-ttu-id="3d8f8-271">Yönetilen nesneler arasındaki boş alan miktarıyla gösterilen yönetilen yığının parçalanması.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-271">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="3d8f8-272">SoS'ta `!dumpheap –type Free` komut, yönetilen nesneler arasındaki boş alan miktarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-272">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="3d8f8-273">Sanal bellek parçalanma (VM) adres alanı, bellek olarak `MEM_FREE`işaretlenmiş olan .</span><span class="sxs-lookup"><span data-stu-id="3d8f8-273">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="3d8f8-274">Windbg çeşitli hata ayıklama komutları kullanarak alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-274">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="3d8f8-275">Aşağıdaki örnekvm alanında parçalanma gösterir:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-275">The following example shows fragmentation in the VM space:</span></span>

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

<span data-ttu-id="3d8f8-276">Çöp toplayıcısının işletim sistemi'nden sık sık yeni yönetilen yığın segmentleri edinmesini ve boş olanları işletim sistemi'ne geri salmasını gerektiren geçici büyük nesnelerden kaynaklanan VM parçalanmasını görmek daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-276">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="3d8f8-277">LOH VM parçalanma neden olup olmadığını doğrulamak için, onları aramak kim görmek için [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) ve [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) bir kesme noktası ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-277">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) and [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) to see who call them.</span></span> <span data-ttu-id="3d8f8-278">Örneğin, işletim sistemi 8MBB'den daha büyük sanal bellek parçalarını kimin ayırmaya çalıştığını görmek için aşağıdaki gibi bir kesme noktası ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3d8f8-278">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="3d8f8-279">Bu komut hata ayıklayıcıya girer ve yalnızca [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) 8MB'dan (0x80000) büyük bir ayırma boyutuyla çağrıldığında çağrı yığınını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-279">This command breaks into the debugger and shows the call stack only if [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="3d8f8-280">CLR 2.0, segmentlerin (büyük ve küçük nesne yığınları dahil) sık sık alınıp serbest bırakıldığı senaryolar için yararlı olabilecek *VM Hoarding* adlı bir özellik ekledi.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-280">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarios where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="3d8f8-281">VM Istifleme belirtmek için, barındırma `STARTUP_HOARD_GC_VM` API'si üzerinden çağrılan bir başlangıç bayrağı belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-281">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="3d8f8-282">CLR, boş segmentleri işletim sistemi için geri serbest bırakmak yerine, bu segmentlerde bellek decommits ve bekleme listesine koyar.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-282">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="3d8f8-283">(CLR'nin bunu çok büyük segmentler için yapmadığını unutmayın.) CLR daha sonra bu segmentleri yeni segment isteklerini karşılamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-283">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="3d8f8-284">Uygulamanızın yeni bir segmente ihtiyacı olduğunda, CLR yeterince büyük bir segment bulabilirse bu bekleme listesinden bir tane kullanır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-284">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="3d8f8-285">VM istifleme, bellek özel durumları dışında önlemek için sistemde çalışan baskın uygulamalar olan bazı sunucu uygulamaları gibi zaten edindikleri segmentleri tutmak isteyen uygulamalar için de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-285">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.</span></span>

<span data-ttu-id="3d8f8-286">Uygulamanızın oldukça kararlı bellek kullanımına sahip olduğundan emin olmak için bu özelliği kullandığınızda uygulamanızı dikkatle test etmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="3d8f8-286">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>
