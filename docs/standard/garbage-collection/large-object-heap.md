---
title: Windows sistemlerinde büyük nesne yığın
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: abb1f72a10a4aff448dea22b5c9415111c25eaab
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="19574-102">Windows sistemlerinde büyük nesne yığın</span><span class="sxs-lookup"><span data-stu-id="19574-102">The large object heap on Windows systems</span></span>

<span data-ttu-id="19574-103">.NET Atık toplayıcısının (GC) nesneleri küçük ve büyük nesneleri böler.</span><span class="sxs-lookup"><span data-stu-id="19574-103">The .NET Garbage Collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="19574-104">Bir nesne büyük olduğunda bazı özniteliklerini nesne küçük olup olmadığını daha önemli ölçüde haline gelir.</span><span class="sxs-lookup"><span data-stu-id="19574-104">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="19574-105">Örneğin, buna--öbek herhangi bir yerinde bellekte kopyalama olan--sıkıştırılmasını pahalı olabilir.</span><span class="sxs-lookup"><span data-stu-id="19574-105">For instance, compacting it -- that is, copying it in memory elsewhere on the heap -- can be expensive.</span></span> <span data-ttu-id="19574-106">Bu nedenle, .NET Atık toplayıcısının büyük nesneler büyük nesne yığın (LOH) yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="19574-106">Because of this, the .NET Garbage Collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="19574-107">Bu konuda, büyük nesne Yığın derinliği inceleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="19574-107">In this topic, we'll look at the large object heap in depth.</span></span> <span data-ttu-id="19574-108">Hangi nesne büyük nesne olarak niteleyen, bu büyük nesneler nasıl toplanır ve ne tür performans etkileri büyük nesneler zorunlu tuttukları ele alacağız.</span><span class="sxs-lookup"><span data-stu-id="19574-108">We'll discuss what qualifies an object as a large object, how these large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="19574-109">Bu konu yalnızca Windows sistemlerinde çalışan .NET Core ve .NET Framework içinde büyük nesne yığın açıklar.</span><span class="sxs-lookup"><span data-stu-id="19574-109">This topic discusses the large object heap in the .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="19574-110">.NET uygulamaları diğer platformlarda çalışan LOH kapsamaz.</span><span class="sxs-lookup"><span data-stu-id="19574-110">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a><span data-ttu-id="19574-111">Bir nesne üzerinde büyük nesne yığın nasıl sona erer ve GC bunları nasıl işler?</span><span class="sxs-lookup"><span data-stu-id="19574-111">How an object ends up on the large object heap and how GC handles them</span></span>

<span data-ttu-id="19574-112">Bir nesne 85. 000 bayta eşit veya daha büyük ise, büyük nesne dikkate almıştır.</span><span class="sxs-lookup"><span data-stu-id="19574-112">If an object is greater than or equal to 85,000 bytes, it’s considered a large object.</span></span> <span data-ttu-id="19574-113">Bu sayı, performans ayarlama belirlendi.</span><span class="sxs-lookup"><span data-stu-id="19574-113">This number was determined by performance tuning.</span></span> <span data-ttu-id="19574-114">Bir nesne ayırma isteği için 85. 000 ya da daha fazla bayt olduğunda, çalışma zamanı üzerinde büyük nesne yığın ayırır.</span><span class="sxs-lookup"><span data-stu-id="19574-114">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="19574-115">Bunun ne anlama geldiği anlamak için .NET GC hakkında bazı temelleri incelemek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="19574-115">To understand what this means, it's useful to examine some fundamentals about the .NET GC.</span></span>

<span data-ttu-id="19574-116">.NET Atık toplayıcısının bir kişinin Toplayıcı ' dir.</span><span class="sxs-lookup"><span data-stu-id="19574-116">The .NET Garbage Collector is a generational collector.</span></span> <span data-ttu-id="19574-117">Üç nesil vardır: kuşak 0, 1. nesil ve 2. nesil.</span><span class="sxs-lookup"><span data-stu-id="19574-117">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="19574-118">3 nesli sahip olmak için, çoğu nesneleri dökme gen0 içinde iyi ayarlanmış bir uygulamasında nedenidir.</span><span class="sxs-lookup"><span data-stu-id="19574-118">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="19574-119">Örneğin, istek tamamlandıktan sonra bir sunucu uygulamasında her istekle ilişkili ayırmaları öldürmüş.</span><span class="sxs-lookup"><span data-stu-id="19574-119">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="19574-120">Yürütülen ayırma isteklerini gen1 kolaylaştırır ve öldürmüş vardır.</span><span class="sxs-lookup"><span data-stu-id="19574-120">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="19574-121">Esas olarak, gen1 Küçük yaştaki nesne alanları ve uzun süreli nesne alanları arasında bir tampon görevi görür.</span><span class="sxs-lookup"><span data-stu-id="19574-121">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="19574-122">Küçük nesneleri oluşturma 0 her zaman ayrılır ve kendi ömürleri bağlı olarak, 1. nesil veya generation2 yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="19574-122">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="19574-123">Büyük nesneler, nesil 2 her zaman ayrılır.</span><span class="sxs-lookup"><span data-stu-id="19574-123">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="19574-124">Yalnızca 2. nesil derleme sırasında toplanan çünkü bunlar büyük nesneler 2. nesil ait.</span><span class="sxs-lookup"><span data-stu-id="19574-124">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="19574-125">Bir oluşturma toplandığında, tüm küçük generation(s) de toplanır.</span><span class="sxs-lookup"><span data-stu-id="19574-125">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="19574-126">Örneğin, 1. nesil GC gerçekleştiğinde, her iki nesil 1 ve 0 toplanır.</span><span class="sxs-lookup"><span data-stu-id="19574-126">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="19574-127">Ve 2. nesil GC gerçekleştiğinde, tüm yığın toplanır.</span><span class="sxs-lookup"><span data-stu-id="19574-127">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="19574-128">Bu nedenle, 2. nesil GC olarak da adlandırılan bir *tam GC*.</span><span class="sxs-lookup"><span data-stu-id="19574-128">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="19574-129">2. nesil GC tam GC yerine bu makalede başvuruyor, ancak koşulları birbirinin yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19574-129">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="19574-130">Nesli GC yığını mantıksal bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="19574-130">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="19574-131">Fiziksel olarak, nesneleri Yönetilen yığın segmentlerinde dinamik.</span><span class="sxs-lookup"><span data-stu-id="19574-131">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="19574-132">A *Yönetilen yığın segment* bir öbektir çağırarak OS GC ayırır bellek [VirtualAlloc işlevi](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) yönetilen kod adına.</span><span class="sxs-lookup"><span data-stu-id="19574-132">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) on behalf of managed code.</span></span> <span data-ttu-id="19574-133">CLR yüklendiğinde GC iki ilk öbek kesimi ayırır: küçük nesneleri (küçük nesne yığın veya SOH) için diğeri için büyük nesneler (büyük nesne yığın).</span><span class="sxs-lookup"><span data-stu-id="19574-133">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the Small Object Heap, or SOH), and one for large objects (the Large Object Heap).</span></span>

<span data-ttu-id="19574-134">İstekleri sonra memnun koyarak ayırma yönetilen nesneler üzerinde bu Yönetilen yığın kesimler.</span><span class="sxs-lookup"><span data-stu-id="19574-134">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="19574-135">85. 000 bayt'tan küçük nesneyse için SOH kesiminde yerleştirilir; Aksi halde, bir LOH kesiminde yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="19574-135">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="19574-136">Segment (daha küçük parçalar) daha fazla yapıldığından ve daha fazla nesneleri açtığına ayrılmaz.</span><span class="sxs-lookup"><span data-stu-id="19574-136">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="19574-137">SOH için GC varlığını sürdürmesini nesneleri nesil için öne çıkar.</span><span class="sxs-lookup"><span data-stu-id="19574-137">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="19574-138">Kuşak 0 koleksiyonu varlığını sürdürmesini nesneler artık kuşak 1 nesnelerinin olarak kabul edilir ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="19574-138">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="19574-139">Ancak, eski kuşak varlığını sürdürmesini nesneler hala eski nesil olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="19574-139">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="19574-140">Diğer bir deyişle, 2. nesil gelen survivors 2. nesil nesneleridir; ve LOH gelen survivors (hangi gen2 ile toplanan) LOH nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="19574-140">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span> 

<span data-ttu-id="19574-141">Kullanıcı kodu yalnızca 0 (küçük nesneler) veya (büyük nesneler) LOH oluşturma tahsis edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19574-141">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="19574-142">GC "nesneleri nesil 1 (0 kuşaktan survivors yükselterek) tahsis edebilirsiniz yalnızca" ve (tarafından survivors 1 ve 2 nesli yükseltme) 2. nesil.</span><span class="sxs-lookup"><span data-stu-id="19574-142">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="19574-143">Çöp toplama tetiklendiğinde GC dinamik nesneler arasında izler ve bunları sıkıştırır.</span><span class="sxs-lookup"><span data-stu-id="19574-143">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="19574-144">Ancak sıkıştırma pahalıdır GC *taramalar* LOH; daha sonra büyük nesne ayırma isteklerini karşılamak için yeniden kullanılabilir ölü nesneleri dışında boş bir liste sağlar.</span><span class="sxs-lookup"><span data-stu-id="19574-144">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="19574-145">Bitişik ölü nesneleri bir ücretsiz nesnesine yapılır.</span><span class="sxs-lookup"><span data-stu-id="19574-145">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="19574-146">.NET core ve .NET Framework'ü (.NET Framework 4.5.1 ile başlayarak) dahil <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty="fullname"> belirtmek için LOH kullanıcılara özelliği sırasında sonraki tam engelleme GC düzenlenmiş.</span><span class="sxs-lookup"><span data-stu-id="19574-146">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty="fullname"> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="19574-147">Ve .NET LOH otomatik olarak compact gelecekte karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19574-147">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="19574-148">Bu büyük nesneler ayırmak ve bunlar taşıma emin olmak istiyorsanız, yine bunları sabitleyebilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="19574-148">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="19574-149">Şekil 1 burada GC forms 1. nesil birinci nesil 0 GC sonra bir senaryo gösterilmektedir nerede `Obj1` ve `Obj3` ölü olan ve forms 2. nesil birinci nesil 1 GC sonra burada `Obj2` ve `Obj5` ölü şunlardır.</span><span class="sxs-lookup"><span data-stu-id="19574-149">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="19574-150">Bu ve aşağıdaki rakamları yalnızca gösterim amacıyla olduğunu unutmayın; daha iyi öbek üzerinde olanlar göstermek için çok az sayıda nesneleri içerirler.</span><span class="sxs-lookup"><span data-stu-id="19574-150">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="19574-151">Gerçekte, pek çok nesne, genellikle bir GC ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="19574-151">In reality, many more objects are typically involved in a GC.</span></span>

![Şekil 1: Gen 0 GC ve gen 1 GC](media/loh/loh-figure-1.jpg)   
<span data-ttu-id="19574-153">Şekil 1: Kuşak 0 ve 1. nesil GC.</span><span class="sxs-lookup"><span data-stu-id="19574-153">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="19574-154">Şekil 2 gösterir, 2. nesil GC sonra gördüğünüz `Obj1` ve `Obj2` olan GC forms bitişik boş alanı tarafından akacağını kullanılan bellek tükendi ölü `Obj1` ve `Obj2`, o ayırma isteği karşılamak için kullanıldı için `Obj4`.</span><span class="sxs-lookup"><span data-stu-id="19574-154">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="19574-155">Son nesne sonra boşluk `Obj3`, segmentinin sonunu ayrıca ayırma isteklerini karşılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19574-155">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>
 
![Şekil 2: sonra gen 2 GC](media/loh/loh-figure-2.jpg)  
<span data-ttu-id="19574-157">Şekil 2: sonra 2. nesil GC</span><span class="sxs-lookup"><span data-stu-id="19574-157">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="19574-158">Büyük nesne ayırma isteklerini karşılamak için yeterli boş alan yoksa GC önce işletim sistemi daha fazla bölümlerinin almaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="19574-158">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="19574-159">Başarısız olursa, 2. nesil GC biraz alan boşaltın boşaltma, soluk içinde tetikler.</span><span class="sxs-lookup"><span data-stu-id="19574-159">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="19574-160">1. nesil veya 2. nesil GC sırasında dinamik Nesne üzerlerinde işletim sistemine geri çağırarak sahip atık toplayıcı serbest [VirtualFree işlevi](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="19574-160">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx).</span></span> <span data-ttu-id="19574-161">(Burada gen0/atık toplayıcı bazı burada korumak gen1 canlı, çünkü kaydedilen kısa ömürlü kesiminde uygulamanız içinde hemen ayırma dışında) segmentinin sonunu son Canlı nesnesine sonra kaydı geri alınmış alanıdır.</span><span class="sxs-lookup"><span data-stu-id="19574-161">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="19574-162">Ve bunlar, işletim sistemi veri bunları yeniden diske yazma gerekmez anlamı sıfırlanır olsa boş alanları kaydedilmiş kalır.</span><span class="sxs-lookup"><span data-stu-id="19574-162">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="19574-163">LOH kesimi, yalnızca LOH yalnızca 2. nesil GC'ler sırasında toplanan olduğundan, bu tür bir GC sırasında serbest.</span><span class="sxs-lookup"><span data-stu-id="19574-163">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="19574-164">Şekil 3 burada atık toplayıcı bir segmente (kesim 2) geri işletim sistemi sürümleri ve kalan segmentler hakkında daha fazla alan decommits bir senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="19574-164">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="19574-165">Büyük nesne ayırma isteklerini karşılamak için kesim sonunda kaydı geri alınmış alan kullanması gerekirse, bellek yeniden kaydeder.</span><span class="sxs-lookup"><span data-stu-id="19574-165">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="19574-166">(Bir açıklaması tamamlama ve kaydettikleri için belgelerine bakın [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="19574-166">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx).</span></span>
 
![Şekil 3: LOH gen 2 GC sonra](media/loh/loh-figure-3.jpg)  
<span data-ttu-id="19574-168">Şekil 3: 2. nesil GC sonra LOH</span><span class="sxs-lookup"><span data-stu-id="19574-168">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="19574-169">Ne zaman büyük nesne toplanır?</span><span class="sxs-lookup"><span data-stu-id="19574-169">When is a large object collected?</span></span>

<span data-ttu-id="19574-170">Genel olarak, aşağıdaki 3 aşağıdaki koşullardan biri gerçekleştiğinde bir GC oluşur:</span><span class="sxs-lookup"><span data-stu-id="19574-170">In general, a GC occurs when one of the following following 3 conditions happens:</span></span>

- <span data-ttu-id="19574-171">Ayırma kuşak 0 veya büyük nesne eşiği aşıyor.</span><span class="sxs-lookup"><span data-stu-id="19574-171">Allocation exceeds the generation 0 or large object threshold.</span></span>

   <span data-ttu-id="19574-172">Eşik bir nesil bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="19574-172">The threshold is a property of a generation.</span></span> <span data-ttu-id="19574-173">Çöp toplayıcı nesneleri içine ayırdığında bir oluşturma için bir eşik ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="19574-173">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="19574-174">Eşik aşıldığında, GC üzerinde nesil tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="19574-174">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="19574-175">Küçük veya büyük nesneleri tahsis ettiğinizde, kuşak 0 ve LOH'ın eşikleri, sırasıyla tüketir.</span><span class="sxs-lookup"><span data-stu-id="19574-175">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="19574-176">Çöp toplayıcı 1 ve 2. nesil ayırdığında kendi eşiklerini tüketir.</span><span class="sxs-lookup"><span data-stu-id="19574-176">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="19574-177">Program çalışırken bu eşikler dinamik olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="19574-177">These thresholds are dynamically tuned as the program runs.</span></span>

   <span data-ttu-id="19574-178">Bu normal bir durumdur; yönetilen yığında ayırmalar nedeniyle çoğu GC'ler gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="19574-178">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="19574-179"><xref:System.GC.Collect%2A?displayProperty=nameWithType> Yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="19574-179">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

   <span data-ttu-id="19574-180">Varsa parametresiz <xref:System.GC.Collect?displayProperty=nameWithType> yöntemi çağrıldığında veya başka bir aşırı geçirilen <xref:System.GC.MaxGeneration?displayProperty=nameWithType> bir bağımsız değişken olarak yönetilen yığın geri kalanı ile birlikte LOH toplanır.</span><span class="sxs-lookup"><span data-stu-id="19574-180">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="19574-181">Düşük bellek durumda sistemidir.</span><span class="sxs-lookup"><span data-stu-id="19574-181">The system is in low memory situation.</span></span>

   <span data-ttu-id="19574-182">Çöp toplayıcı OS yüksek bellek bildirimi aldığında bu oluşur.</span><span class="sxs-lookup"><span data-stu-id="19574-182">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="19574-183">2. nesil GC yapılması üretken olmasını atık toplayıcı düşündüğü, bir tetikler.</span><span class="sxs-lookup"><span data-stu-id="19574-183">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="19574-184">LOH performans etkileri</span><span class="sxs-lookup"><span data-stu-id="19574-184">LOH Performance Implications</span></span>

<span data-ttu-id="19574-185">Ayırmalar büyük nesne yığın üzerinde aşağıdaki yollarla performansını etkiler.</span><span class="sxs-lookup"><span data-stu-id="19574-185">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="19574-186">Maliyet ayırma.</span><span class="sxs-lookup"><span data-stu-id="19574-186">Allocation cost.</span></span>

   <span data-ttu-id="19574-187">CLR verir bellek her yeni nesne için temizlenir garantisi yapar.</span><span class="sxs-lookup"><span data-stu-id="19574-187">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="19574-188">Bu, büyük nesne ayırma maliyetini tamamen (GC tetikler sürece) temizleyerek bellek tarafından hâkim anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="19574-188">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="19574-189">Bir bayt temizlemek için 2 döngüleri geçen en küçük büyük nesne temizlemek için 170,000 döngüleri kazanır.</span><span class="sxs-lookup"><span data-stu-id="19574-189">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="19574-190">2 GHz makine 16 MB nesnesinde memmory temizleme yaklaşık 16ms alır.</span><span class="sxs-lookup"><span data-stu-id="19574-190">Clearing the memmory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="19574-191">Bunun yerine büyük bir maliyet olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="19574-191">That's a rather large cost.</span></span>

- <span data-ttu-id="19574-192">Maliyet koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="19574-192">Collection cost.</span></span>

   <span data-ttu-id="19574-193">Herhangi birinin eşik aşılırsa LOH ve 2. nesil birlikte toplanır olduğundan, 2. nesil koleksiyonu tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="19574-193">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="19574-194">2 koleksiyonu nedeniyle LOH tetiklenir oluşturma, 2. nesil mutlaka GC sonra çok daha küçük olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="19574-194">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="19574-195">2. nesil üzerinde kadar veri değilse, bunun en az etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="19574-195">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="19574-196">Ancak 2. nesil büyükse, birçok 2. nesil GC'ler tetiklenen durumunda performans sorunlarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="19574-196">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="19574-197">Birçok büyük nesneler çok geçici temeline göre ayrılır ve büyük SOH varsa GC'ler yapılması çok fazla zaman harcama.</span><span class="sxs-lookup"><span data-stu-id="19574-197">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="19574-198">Ayrıca, ayırma maliyet gerçekten ayırma ve izin vererek gerçekten büyük nesnelerin Git tutmak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19574-198">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="19574-199">Başvuru türleri öğelerle dizi.</span><span class="sxs-lookup"><span data-stu-id="19574-199">Array elements with reference types.</span></span>

   <span data-ttu-id="19574-200">Çok büyük nesneler üzerinde LOH genellikle (gerçekten büyük bir örnek nesne sağlamak için çok nadir) dizidir.</span><span class="sxs-lookup"><span data-stu-id="19574-200">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="19574-201">Dizi öğeleri ise isteğe bağlı olarak başvuru-zengin, öğeleri değilseniz, mevcut olmayan bir maliyet oluşturur başvuru zengin.</span><span class="sxs-lookup"><span data-stu-id="19574-201">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="19574-202">Öğe tüm başvuruları içermiyorsa, atık toplayıcı dizi boyunca hiç gitmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="19574-202">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="19574-203">Bir ikili ağacı düğümleri depolamak için bir dizi kullanırsanız, örneğin, uygulamak için tek bir düğümün sağ ve sol düğüm gerçek düğümleri tarafından başvurmak için yoludur:</span><span class="sxs-lookup"><span data-stu-id="19574-203">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

   ```csharp
   class Node
   {
      Data d;
      Node left;
      Node right;
   };

   Node[] binary_tr = new Node [num_nodes];
   ```

   <span data-ttu-id="19574-204">Varsa `num_nodes` olan öğesi başına en az iki başvuru gitmesi büyük, atık toplayıcı gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="19574-204">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="19574-205">Sağ ve sol düğümler dizinini depolamak için alternatif bir yaklaşım şöyledir:</span><span class="sxs-lookup"><span data-stu-id="19574-205">An alternative approach is to store the index of the right and the left nodes:</span></span>

   ```csharp
   class Node
   {
      Data d;
      uint left_index;
      uint right_index;
   } ;
   ```

   <span data-ttu-id="19574-206">Sol düğümün verileri olarak başvuran yerine `left.d`, olarak başvuran `binary_tr[left_index].d`.</span><span class="sxs-lookup"><span data-stu-id="19574-206">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="19574-207">Ve atık toplayıcı sol ve sağ düğüm için tüm başvuruları bakmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="19574-207">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="19574-208">Üç dışında ilk iki genellikle üçüncü daha önemli faktörlerdir.</span><span class="sxs-lookup"><span data-stu-id="19574-208">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="19574-209">Bu nedenle, geçici olanları ayırma yerine yeniden büyük nesneler havuzu ayırma öneririz.</span><span class="sxs-lookup"><span data-stu-id="19574-209">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span> 

## <a name="collecting-performance-data-for-the-loh"></a><span data-ttu-id="19574-210">LOH için performans verilerini toplama</span><span class="sxs-lookup"><span data-stu-id="19574-210">Collecting performance data for the LOH</span></span>

<span data-ttu-id="19574-211">Belirli bir alan için performans verilerini toplama önce aşağıdakileri yapmış olduğunuz:</span><span class="sxs-lookup"><span data-stu-id="19574-211">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="19574-212">Bu alanında aramanız gereken kanıt bulundu.</span><span class="sxs-lookup"><span data-stu-id="19574-212">Found evidence that you should be looking at this area.</span></span>

1. <span data-ttu-id="19574-213">Gördüğünüz performans sorunu açıklayan, herhangi bir şey bulmadan bildiğiniz diğer alanlarına tükendi.</span><span class="sxs-lookup"><span data-stu-id="19574-213">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="19574-214">Blog bakın [bir çözüm bulmak denemeden önce sorunu anlamak](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) bellek ve CPU temelleri hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="19574-214">See the blog [Understand the problem before you try to find a solution](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="19574-215">LOH performans verilerini toplamak için aşağıdaki araçları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="19574-215">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="19574-216">.NET CLR bellek performansı sayaçları</span><span class="sxs-lookup"><span data-stu-id="19574-216">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="19574-217">ETW olayları</span><span class="sxs-lookup"><span data-stu-id="19574-217">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="19574-218">Hata ayıklayıcı</span><span class="sxs-lookup"><span data-stu-id="19574-218">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="19574-219">.NET CLR bellek performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="19574-219">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="19574-220">Bu performans sayaçlarını performans sorunları incelemeye bir iyi ilk adımı genellikle olan (kullanmanızı öneririz, ancak [ETW olayları](#etw)).</span><span class="sxs-lookup"><span data-stu-id="19574-220">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw)).</span></span> <span data-ttu-id="19574-221">Şekil 4'te gösterildiği gibi istediğiniz sayaçları ekleyerek Performans İzleyicisi'ni yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="19574-221">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="19574-222">LOH için uygun olan ve güçlüklerdir:</span><span class="sxs-lookup"><span data-stu-id="19574-222">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="19574-223">**\# Gen 2 koleksiyonları**</span><span class="sxs-lookup"><span data-stu-id="19574-223">**\# Gen 2 Collections**</span></span>

   <span data-ttu-id="19574-224">2. nesil GC'ler işlem başlatıldığından bu yana gerçekleşen sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="19574-224">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="19574-225">(Tam atık toplama olarak da bilinir) 2. nesil koleksiyonunun sonuna sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="19574-225">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="19574-226">Bu sayaç gözlenen son değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="19574-226">This counter displays the last observed value.</span></span>

- <span data-ttu-id="19574-227">**Büyük nesne yığın boyutu**</span><span class="sxs-lookup"><span data-stu-id="19574-227">**Large Object Heap size**</span></span>

   <span data-ttu-id="19574-228">Geçerli boyut boş alanı, LOH dahil olmak üzere bayt cinsinden görüntüler.</span><span class="sxs-lookup"><span data-stu-id="19574-228">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="19574-229">Bu sayaç her ayırma değil, bir atık toplama işleminin sonunda güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="19574-229">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="19574-230">Performans İzleyicisi (perfmon.exe) performans sayaçları aramak için genel bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="19574-230">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="19574-231">İlgilendiğiniz işlemler için ilginç sayaç eklemek için "Sayaç Ekle" kullanın.</span><span class="sxs-lookup"><span data-stu-id="19574-231">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="19574-232">Şekil 4'te gösterildiği gibi bir günlük dosyasına performans sayacı verilerini kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19574-232">You can save the performance counter data to a log file, as Figure 4 shows.</span></span>

![Şekil 4: performans sayaçları ekleniyor.](media/loh/perfcounter.png)    
<span data-ttu-id="19574-234">Şekil 4: 2. nesil GC sonra LOH</span><span class="sxs-lookup"><span data-stu-id="19574-234">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="19574-235">Performans sayaçları de bir program aracılığıyla sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="19574-235">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="19574-236">Birçok kişi bunları kendi rutin sınama işleminin bir parçası olarak bu şekilde toplayın.</span><span class="sxs-lookup"><span data-stu-id="19574-236">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="19574-237">Sıra dışıdır olan değerleri sayaçlarıyla nokta, bunlar başka yöntemler ile araştırmaya yardımcı olmak için ayrıntılı veri almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="19574-237">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="19574-238">ETW kadar daha zengin bilgi sağladığından, ETW olayları performans yerine kullanılacak sayaçları olduğunu, öneririz.</span><span class="sxs-lookup"><span data-stu-id="19574-238">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw"></a><span data-ttu-id="19574-239">ETW</span><span class="sxs-lookup"><span data-stu-id="19574-239">ETW</span></span>

<span data-ttu-id="19574-240">Çöp toplayıcı ETW olayları öbek ne yaptığını anlamanıza yardımcı olması için zengin bir dizi sağlar ve neden.</span><span class="sxs-lookup"><span data-stu-id="19574-240">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="19574-241">Aşağıdaki blog gönderileri toplamak ve GC olayları ETW ile anlamak nasıl göster:</span><span class="sxs-lookup"><span data-stu-id="19574-241">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="19574-242">GC ETW olayları - 1 </span><span class="sxs-lookup"><span data-stu-id="19574-242">GC ETW Events - 1 </span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/22/gc-etw-events.aspx)

- [<span data-ttu-id="19574-243">GC ETW olayları - 2</span><span class="sxs-lookup"><span data-stu-id="19574-243">GC ETW Events - 2</span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/25/gc-etw-events-2.aspx)

- [<span data-ttu-id="19574-244">GC ETW olayları - 3</span><span class="sxs-lookup"><span data-stu-id="19574-244">GC ETW Events - 3</span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/25/gc-etw-events-3.aspx) 

- [<span data-ttu-id="19574-245">GC ETW olayları - 4</span><span class="sxs-lookup"><span data-stu-id="19574-245">GC ETW Events - 4</span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/30/gc-etw-events-4.aspx)

<span data-ttu-id="19574-246">Aşırı nesil 2 GC'ler tarafından geçici LOH ayırmaları nedeni belirlemek için GC'ler için tetikleyici neden sütununa bakın.</span><span class="sxs-lookup"><span data-stu-id="19574-246">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="19574-247">Yalnızca geçici büyük nesneler tarafından ayrılan basit bir test için ETW olaylarına aşağıdaki bilgi toplayabilirsiniz [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) komut satırı:</span><span class="sxs-lookup"><span data-stu-id="19574-247">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="19574-248">Sonuç şöyle olur:</span><span class="sxs-lookup"><span data-stu-id="19574-248">The result is something like this:</span></span>
 
![Şekil 5: ETW olayları PerfView kullanarak inceleniyor](media/loh/perfview.png)  
<span data-ttu-id="19574-250">Şekil 5: PerfView kullanılarak gösterilen ETW olayları</span><span class="sxs-lookup"><span data-stu-id="19574-250">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="19574-251">Gördüğünüz gibi 2. nesil GC'ler tüm GC'ler olan ve tüm büyük nesne ayırma bu GC tetiklenen anlamına gelir AllocLarge tarafından tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="19574-251">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="19574-252">Bu ayırmaları geçici olduğunu biliyoruz çünkü **LOH hayatta kalma oranı %** sütun %1 söyler.</span><span class="sxs-lookup"><span data-stu-id="19574-252">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="19574-253">Bu büyük nesneler ayrılan size ek ETW olayları toplayabilir.</span><span class="sxs-lookup"><span data-stu-id="19574-253">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="19574-254">Aşağıdaki komut satırı:</span><span class="sxs-lookup"><span data-stu-id="19574-254">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="19574-255">yaklaşık her 100 k değerinde ayırmaları harekete AllocationTick olay toplar.</span><span class="sxs-lookup"><span data-stu-id="19574-255">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="19574-256">Diğer bir deyişle, her zaman büyük nesne ayrılmış bir olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="19574-256">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="19574-257">Ayrılmış büyük nesneleri callstacks Göster GC yığın ayırma görünümler birini sonra arayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="19574-257">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>
 
![Şekil 6: Bir GC yığın ayırma görünümü](media/loh/perfview2.png)  
<span data-ttu-id="19574-259">Şekil 6: Bir GC yığın ayırma görünümü</span><span class="sxs-lookup"><span data-stu-id="19574-259">Figure 6: A GC Heap Alloc view</span></span>
 
<span data-ttu-id="19574-260">Gördüğünüz gibi yalnızca büyük nesneleri ayırır çok basit bir sınama budur kendi `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="19574-260">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="19574-261">Hata ayıklayıcı</span><span class="sxs-lookup"><span data-stu-id="19574-261">A debugger</span></span>

<span data-ttu-id="19574-262">Sahip olduğunuz şey bir bellek dökümü ve nesneleri gerçekten üzerinde LOH nelerdir aramak gereken, kullanabileceğiniz [SoS hata ayıklayıcı uzantısı](http://msdn2.microsoft.com/ms404370.aspx) .NET tarafından sağlanan.</span><span class="sxs-lookup"><span data-stu-id="19574-262">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](http://msdn2.microsoft.com/ms404370.aspx) provided by .NET.</span></span> 

> [!NOTE]
> <span data-ttu-id="19574-263">Bu bölümde belirtilen hata ayıklama komutları için geçerli olan [Windows hata ayıklayıcıları](http://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span><span class="sxs-lookup"><span data-stu-id="19574-263">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](http://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="19574-264">Aşağıdaki LOH çözümleme gelen örnek çıkış şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="19574-264">The following shows sample output from analyzing the LOH:</span></span>

```
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

<span data-ttu-id="19574-265">LOH yığın boyutudur (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bayt.</span><span class="sxs-lookup"><span data-stu-id="19574-265">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="19574-266">Adresleri 023e1000 ve 033db630 arasında 8,008,736 bayt dizisi tarafından kapladığı <xref:System.Object?displayProperty=fullName> nesneleri 6,663,696 bayt dizisi tarafından kapladığı <xref:System.Byte?displayProperty=nameWithType> nesneleri ve 2,081,792 bayt tarafından boş alanı dolu.</span><span class="sxs-lookup"><span data-stu-id="19574-266">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=fullName> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="19574-267">Bazı durumlarda, hata ayıklayıcı LOH toplam boyutu 85. 000 bayt'tan küçük olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="19574-267">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="19574-268">Çalışma zamanı kendisini geniş bir nesne daha küçük olan bazı nesneler ayrılacak LOH kullandığından bu gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="19574-268">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="19574-269">LOH sıkıştırılmış değil, bazen LOH parçalanma bir kaynak olarak thoought olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="19574-269">Because the LOH is not compacted, sometimes the LOH is thoought to be the source of fragmentation.</span></span> <span data-ttu-id="19574-270">Parçalanma anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="19574-270">Fragmentation means:</span></span>

- <span data-ttu-id="19574-271">Yönetilen nesneler arasında boş alan miktarı tarafından gösterilen Yönetilen yığın parçalanma.</span><span class="sxs-lookup"><span data-stu-id="19574-271">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="19574-272">SoS içinde `!dumpheap –type Free` komutu, yönetilen nesneler arasında boş alan miktarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="19574-272">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="19574-273">Bellek sanal bellek (VM) adres alanının parçalanması olarak işaretli `MEM_FREE`.</span><span class="sxs-lookup"><span data-stu-id="19574-273">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="19574-274">İçinde windbg çeşitli hata ayıklayıcı komutlarını kullanarak elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19574-274">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="19574-275">Aşağıdaki örnek, VM alanı parçalanma gösterir:</span><span class="sxs-lookup"><span data-stu-id="19574-275">The following example shows fragmentation in the VM space:</span></span>

   ```
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

<span data-ttu-id="19574-276">Sık sık yeni edinmeye atık toplayıcı yığın kesimleri OS yönetilen ve boş olanları işletim sistemine geri yayın gerektiren geçici büyük nesneler nedeni VM parçalanma görmek için daha yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="19574-276">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="19574-277">LOH VM parçalanma neden olup olmadığını doğrulamak için bir kesme noktası ayarlayabilirsiniz [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) ve [VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) kimin çağrı görmek için.</span><span class="sxs-lookup"><span data-stu-id="19574-277">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) and [VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) to see who call them.</span></span> <span data-ttu-id="19574-278">Örneğin, kimin OS 8MBB büyük sanal bellek parçalara ayırmaya çalıştığını görmek için böyle bir kesme noktası ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="19574-278">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="19574-279">Bu komut ayıklayıcıya keser ve çağrı yığını eksikse gösterir [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) bir ayırma boyutu (0x800000) 8 MB'den büyük olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="19574-279">This command breaks into the debugger and shows the callstack only if [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="19574-280">CLR 2.0 eklenen adlı bir özelliği *VM Hoarding* , scenarious için yararlı olabilir burada kesim (yığın nesnesi büyük ve küçük üzerinde de dahil olmak üzere) sık edinilen ve yayımlanan.</span><span class="sxs-lookup"><span data-stu-id="19574-280">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarious where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="19574-281">Adlı bir başlangıç bayrak belirttiğiniz VM Hoarding belirtmek için `STARTUP_HOARD_GC_VM` barındırma API aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="19574-281">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="19574-282">İşletim sistemi boş segmentlere geri serbest bırakma, yerine CLR bu kesimler belleği decommits ve bunları bir bekleme listesine koyar.</span><span class="sxs-lookup"><span data-stu-id="19574-282">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="19574-283">(CLR bu çok büyük kesimine yönelik işlemi gerçekleştirmeyen unutmayın.) CLR daha sonra yeni segment isteklerini karşılamak için bu kesimler kullanır.</span><span class="sxs-lookup"><span data-stu-id="19574-283">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="19574-284">Kadar büyük olan bir bulabilirsiniz, uygulamanızın yeni bir segment gerektiğini başlattığınızda bekleme bu listeden bir CLR kullanır.</span><span class="sxs-lookup"><span data-stu-id="19574-284">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="19574-285">VM hoarding, bunlar zaten, yetersiz bellek özel durumları önlemek için bu sistemde çalışan baskın uygulamaların bazı sunucu uygulamaları gibi edinilen kesimleri üzerine tutmak istediğiniz uygulamalar için de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="19574-285">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.</span></span>

<span data-ttu-id="19574-286">Olgunluğa bellek kullanımı, uygulamanızın sağlamak için bu özelliği kullandığınızda, dikkatle uygulamanızı sınamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="19574-286">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>
