---
title: Bellek ve yayılmalar
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbfd091c821f59febfc8c7a203334454e7b59c12
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666430"
---
# <a name="memory--and-span-related-types"></a><span data-ttu-id="947b9-102">Bellek ve yayılma ile ilgili türler</span><span class="sxs-lookup"><span data-stu-id="947b9-102">Memory- and span-related types</span></span>

<span data-ttu-id="947b9-103">.NET Core 2,1 ' den itibaren, .NET, isteğe bağlı, kesin olarak belirlenmiş bir bellek bölgesini temsil eden bir dizi ilişkili tür içerir.</span><span class="sxs-lookup"><span data-stu-id="947b9-103">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly-typed region of arbitrary memory.</span></span> <span data-ttu-id="947b9-104">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="947b9-104">These include:</span></span>

- <span data-ttu-id="947b9-105"><xref:System.Span%601?displayProperty=nameWithType>, belleğin bitişik bir bölgesine erişmek için kullanılan bir tür.</span><span class="sxs-lookup"><span data-stu-id="947b9-105"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="947b9-106">Bir <xref:System.Span%601> örnek `T` türünde<xref:System.String>bir dizi,,, [stackalloc](../../csharp/language-reference/operators/stackalloc.md)ile ayrılmış bir arabellek veya yönetilmeyen bellek işaretçisi tarafından yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="947b9-106">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="947b9-107">Yığına ayrılması gerektiğinden, bir dizi kısıtlamaya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="947b9-107">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="947b9-108">Örneğin, bir sınıftaki bir alan türünde <xref:System.Span%601>olamaz, ya da zaman uyumsuz işlemlerde dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="947b9-108">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="947b9-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, <xref:System.Span%601> yapının sabit bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="947b9-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="947b9-110"><xref:System.Memory%601?displayProperty=nameWithType>, yığın yerine yönetilen yığında ayrılan belleğin bitişik bir bölgesi.</span><span class="sxs-lookup"><span data-stu-id="947b9-110"><xref:System.Memory%601?displayProperty=nameWithType>, a contiguous region of memory that is allocated on the managed heap rather than the stack.</span></span> <span data-ttu-id="947b9-111">Bir <xref:System.Memory%601> örnek, `T` veya<xref:System.String>türünde bir dizi tarafından yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="947b9-111">A <xref:System.Memory%601> instance can be backed by an array of type `T` or a <xref:System.String>.</span></span> <span data-ttu-id="947b9-112">Yönetilen yığında depolanabileceğinden, <xref:System.Memory%601> <xref:System.Span%601>kısıtlamaları yoktur.</span><span class="sxs-lookup"><span data-stu-id="947b9-112">Because it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="947b9-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, <xref:System.Memory%601> yapının sabit bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="947b9-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="947b9-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, bir bellek havuzundan bir sahibe kesin olarak belirlenmiş bellek blokları ayıran.</span><span class="sxs-lookup"><span data-stu-id="947b9-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly-typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="947b9-115"><xref:System.Buffers.IMemoryOwner%601>örnekler, çağırarak havuzdan geri dönerek yeniden <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>kullanıma sunularak havuza eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="947b9-115"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="947b9-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, bir bellek bloğunun sahibini temsil eder ve ömrü yönetimini denetler.</span><span class="sxs-lookup"><span data-stu-id="947b9-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="947b9-117"><xref:System.Buffers.MemoryManager%601>, güvenli işleyiciler gibi ek türler tarafından desteklenen için uygulamasının <xref:System.Memory%601> <xref:System.Memory%601> yerini değiştirmek üzere kullanılabilecek bir soyut temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="947b9-117"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="947b9-118"><xref:System.Buffers.MemoryManager%601>, gelişmiş senaryolar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="947b9-118"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="947b9-119"><xref:System.ArraySegment%601>, belirli bir dizinden başlayarak belirli sayıda dizi öğesi için sarmalayıcı.</span><span class="sxs-lookup"><span data-stu-id="947b9-119"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="947b9-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, dizeler, diziler ve dizi segmentlerini <xref:System.Memory%601> bloklara dönüştürmek için uzantı yöntemleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="947b9-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="947b9-121">Daha önceki çerçeveler <xref:System.Span%601> için ve <xref:System.Memory%601> [System. Memory NuGet paketinde](https://www.nuget.org/packages/System.Memory/)kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="947b9-121">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="947b9-122">Daha fazla bilgi için bkz <xref:System.Buffers?displayProperty=nameWithType> . ad alanı.</span><span class="sxs-lookup"><span data-stu-id="947b9-122">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="947b9-123">Bellek ve yayılma ile çalışma</span><span class="sxs-lookup"><span data-stu-id="947b9-123">Working with memory and span</span></span>

<span data-ttu-id="947b9-124">Bellek ve yayılma ile ilgili türler genellikle verileri bir işlem ardışık düzeninde depolamak için kullanıldığından, geliştiricilerin, <xref:System.Span%601> <xref:System.Memory%601>ve ile ilgili türleri kullanırken en iyi yöntemler kümesini izlemesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="947b9-124">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="947b9-125">Bu en iyi uygulamalar, [\<bellek t > ' de belgelenmiştir\<ve > Kullanım yönergeleri ' ne yayılamaz](memory-t-usage-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="947b9-125">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="947b9-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="947b9-126">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
