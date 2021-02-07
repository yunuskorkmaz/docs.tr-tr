---
description: 'Daha fazla bilgi edinin: bellek ve yayılma ile ilgili türler'
title: Bellek ve yayılmalar
ms.date: 10/03/2018
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: c151632db0fdfff388f1aba95fd9b0edc940ae0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731701"
---
# <a name="memory--and-span-related-types"></a><span data-ttu-id="d331a-103">Bellek ve yayılma ile ilgili türler</span><span class="sxs-lookup"><span data-stu-id="d331a-103">Memory- and span-related types</span></span>

<span data-ttu-id="d331a-104">.NET Core 2,1 ' den itibaren, .NET, rastgele bellek içeren, bitişik ve kesin olarak belirlenmiş bir bölgeyi temsil eden bir dizi ilişkili tür içerir.</span><span class="sxs-lookup"><span data-stu-id="d331a-104">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly typed region of arbitrary memory.</span></span> <span data-ttu-id="d331a-105">Bu modüller şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d331a-105">These include:</span></span>

- <span data-ttu-id="d331a-106"><xref:System.Span%601?displayProperty=nameWithType>, belleğin bitişik bir bölgesine erişmek için kullanılan bir tür.</span><span class="sxs-lookup"><span data-stu-id="d331a-106"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="d331a-107">Bir <xref:System.Span%601> örnek türünde bir dizi, `T` <xref:System.String> ,, [stackalloc](../../csharp/language-reference/operators/stackalloc.md)ile ayrılmış bir arabellek veya yönetilmeyen bellek işaretçisi tarafından yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="d331a-107">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="d331a-108">Yığına ayrılması gerektiğinden, bir dizi kısıtlamaya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d331a-108">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="d331a-109">Örneğin, bir sınıftaki bir alan türünde olamaz <xref:System.Span%601> , ya da zaman uyumsuz işlemlerde dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="d331a-109">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="d331a-110"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, yapının sabit bir sürümüdür <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="d331a-110"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="d331a-111"><xref:System.Memory%601?displayProperty=nameWithType>, bitişik bellek bölgesi üzerinde bir sarmalayıcı.</span><span class="sxs-lookup"><span data-stu-id="d331a-111"><xref:System.Memory%601?displayProperty=nameWithType>, a wrapper over a contiguous region of memory.</span></span> <span data-ttu-id="d331a-112">Bir <xref:System.Memory%601> örnek `T` , bir dizi türü veya bir <xref:System.String> veya bir bellek Yöneticisi tarafından yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="d331a-112">A <xref:System.Memory%601> instance can be backed by an array of type `T`, or a <xref:System.String>, or a memory manager.</span></span> <span data-ttu-id="d331a-113">Yönetilen yığında depolanabileceği <xref:System.Memory%601> için, kısıtlamaları yoktur <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="d331a-113">As it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="d331a-114"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, yapının sabit bir sürümüdür <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="d331a-114"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="d331a-115"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, bellek havuzundan kesin olarak belirlenmiş bellek bloklarını Sahibe ayırır.</span><span class="sxs-lookup"><span data-stu-id="d331a-115"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="d331a-116"><xref:System.Buffers.IMemoryOwner%601> örnekler, çağırarak havuzdan <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> geri dönerek yeniden kullanıma sunularak havuza eklenebilir <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d331a-116"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="d331a-117"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, bir bellek bloğunun sahibini temsil eder ve ömrü yönetimini denetler.</span><span class="sxs-lookup"><span data-stu-id="d331a-117"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="d331a-118"><xref:System.Buffers.MemoryManager%601>, <xref:System.Memory%601> <xref:System.Memory%601> güvenli işleyiciler gibi ek türler tarafından desteklenen için uygulamasının yerini değiştirmek üzere kullanılabilecek bir soyut temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="d331a-118"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="d331a-119"><xref:System.Buffers.MemoryManager%601> , gelişmiş senaryolar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d331a-119"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="d331a-120"><xref:System.ArraySegment%601>, belirli bir dizinden başlayarak belirli sayıda dizi öğesi için sarmalayıcı.</span><span class="sxs-lookup"><span data-stu-id="d331a-120"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="d331a-121"><xref:System.MemoryExtensions?displayProperty=nameWithType>, dizeler, diziler ve dizi segmentlerini bloklara dönüştürmek için uzantı yöntemleri koleksiyonu <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="d331a-121"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

<span data-ttu-id="d331a-122"><xref:System.Span%601?displayProperty=nameWithType>, <xref:System.Memory%601?displayProperty=nameWithType> , ve salt okunur karşılıkları, bellek kopyalamayı veya yönetilen yığında gereken süreden daha fazlasını ayırmayı önlemek için bir algoritma oluşturulmasına olanak tanımak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d331a-122"><xref:System.Span%601?displayProperty=nameWithType>, <xref:System.Memory%601?displayProperty=nameWithType>, and their readonly counterparts are designed to allow the creation of algorithms that avoid copying memory or allocating on the managed heap more than necessary.</span></span> <span data-ttu-id="d331a-123">Bunların oluşturulması (ya da `Slice` oluşturucuları aracılığıyla), temeldeki arabelleklerin yinelenmesiyle ilgili değildir: yalnızca Sarmalanan belleğin "görünümünü" temsil eden ilgili başvurular ve uzaklıklar güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d331a-123">Creating them (either via `Slice` or their constructors) does not involve duplicating the underlying buffers: only the relevant references and offsets, which represent the "view" of the wrapped memory, are updated.</span></span>

> [!NOTE]
> <span data-ttu-id="d331a-124">Daha önceki çerçeveler için <xref:System.Span%601> ve <xref:System.Memory%601> [System. Memory NuGet paketinde](https://www.nuget.org/packages/System.Memory/)kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d331a-124">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="d331a-125">Daha fazla bilgi için bkz <xref:System.Buffers?displayProperty=nameWithType> . ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d331a-125">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="d331a-126">Bellek ve yayılma ile çalışma</span><span class="sxs-lookup"><span data-stu-id="d331a-126">Working with memory and span</span></span>

<span data-ttu-id="d331a-127">Bellek ve yayılma ile ilgili türler genellikle verileri bir işlem ardışık düzeninde depolamak için kullanıldığından, geliştiricilerin <xref:System.Span%601> , <xref:System.Memory%601> ve ile ilgili türleri kullanırken en iyi yöntemler kümesini izlemesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d331a-127">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="d331a-128">Bu en iyi uygulamalar [bellek \<T> ve yayma \<T> Kullanım yönergeleri](memory-t-usage-guidelines.md)bölümünde belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d331a-128">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d331a-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d331a-129">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
