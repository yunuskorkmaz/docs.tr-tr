---
title: Bellek ve yayılma
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ada6003cd6d1cd19036c42a3d0d976e18568f3a
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833966"
---
# <a name="memory--and-span-related-types"></a><span data-ttu-id="4b800-102">Bellek ve aralık ilgili türler</span><span class="sxs-lookup"><span data-stu-id="4b800-102">Memory- and span-related types</span></span>

<span data-ttu-id="4b800-103">.NET, .NET Core 2.1 ile başlayarak, bir dizi bitişik, kesin türü belirtilmiş rastgele bir bellek bölgesini temsil eden birbiriyle türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4b800-103">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly-typed region of arbitrary memory.</span></span> <span data-ttu-id="4b800-104">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4b800-104">These include:</span></span>

- <span data-ttu-id="4b800-105"><xref:System.Span%601?displayProperty=nameWithType>, bitişik bellek bölgesini erişmek için kullanılan bir tür.</span><span class="sxs-lookup"><span data-stu-id="4b800-105"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="4b800-106">A <xref:System.Span%601> örneği bir dizi türü tarafından desteklenen `T`, <xref:System.String>, arabellek ile ayrılan [stackalloc](~/docs/csharp/language-reference/operators/stackalloc.md), veya yönetilmeyen bellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4b800-106">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](~/docs/csharp/language-reference/operators/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="4b800-107">Yığında ayrılacak olduğundan, bazı kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="4b800-107">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="4b800-108">Örneğin, bir alanın bir sınıf türünde olamaz <xref:System.Span%601>, ne de aralık içinde zaman uyumsuz işlemleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4b800-108">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="4b800-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, sabit bir sürümünü <xref:System.Span%601> yapısı.</span><span class="sxs-lookup"><span data-stu-id="4b800-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="4b800-110"><xref:System.Memory%601?displayProperty=nameWithType>, bölgesine bitişik bir yığın yerine yönetilen yığında ayrılan bellek.</span><span class="sxs-lookup"><span data-stu-id="4b800-110"><xref:System.Memory%601?displayProperty=nameWithType>, a contiguous region of memory that is allocated on the managed heap rather than the stack.</span></span> <span data-ttu-id="4b800-111">A <xref:System.Memory%601> örneği bir dizi türü tarafından desteklenen `T` veya <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="4b800-111">A <xref:System.Memory%601> instance can be backed by an array of type `T` or a <xref:System.String>.</span></span> <span data-ttu-id="4b800-112">Yönetilen yığında depolanmış çünkü <xref:System.Memory%601> sınırlamaları hiçbirinin <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="4b800-112">Because it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="4b800-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, sabit bir sürümünü <xref:System.Memory%601> yapısı.</span><span class="sxs-lookup"><span data-stu-id="4b800-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="4b800-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, hangi ayırır bellek blokları kesin türü belirtilmiş bir bellek havuzundan sahip.</span><span class="sxs-lookup"><span data-stu-id="4b800-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly-typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="4b800-115"><xref:System.Buffers.IMemoryOwner%601> örnekleri gibi verilere dayanarak havuzdan çağırarak <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> ve geri çağırarak havuzuna serbest <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4b800-115"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="4b800-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, bir bellek bloğu sahibi temsil eder ve kendi ömrü Yönetimi denetler.</span><span class="sxs-lookup"><span data-stu-id="4b800-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="4b800-117"><xref:System.Buffers.MemoryManager%601>, uygulamasını değiştirmek için kullanılan bir soyut temel sınıf <xref:System.Memory%601> böylece <xref:System.Memory%601> güvenli tanıtıcıları gibi ek türleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4b800-117"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="4b800-118"><xref:System.Buffers.MemoryManager%601> Gelişmiş senaryolar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4b800-118"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="4b800-119"><xref:System.ArraySegment%601>, belirli bir dizinden başlayarak bir dizi öğeleri belirli bir dizi için bir sarmalayıcı.</span><span class="sxs-lookup"><span data-stu-id="4b800-119"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="4b800-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, dizeler, diziler ve dizi segmentlere dönüştürmek için genişletme yöntemleri koleksiyonunu <xref:System.Memory%601> engeller.</span><span class="sxs-lookup"><span data-stu-id="4b800-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="4b800-121">Önceki çerçeveler için <xref:System.Span%601> ve <xref:System.Memory%601> kullanılabilir [System.Memory NuGet paketi](https://www.nuget.org/packages/System.Memory/).</span><span class="sxs-lookup"><span data-stu-id="4b800-121">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="4b800-122">Daha fazla bilgi için <xref:System.Buffers?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4b800-122">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="4b800-123">Bellek ve yayılma ile çalışma</span><span class="sxs-lookup"><span data-stu-id="4b800-123">Working with memory and span</span></span>

<span data-ttu-id="4b800-124">Bellek ve aralık ilgili türler genellikle bir işleme işlem hattı, verileri depolamak için kullanıldığından, geliştiriciler kullanırken birtakım en iyi uygulamaları izlemeniz önemlidir <xref:System.Span%601>, <xref:System.Memory%601>ve ilgili türler.</span><span class="sxs-lookup"><span data-stu-id="4b800-124">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="4b800-125">Bu en iyi belgelenmiştir [bellek\<T > ve aralık\<T > kullanım yönergeleri](memory-t-usage-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="4b800-125">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4b800-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b800-126">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
