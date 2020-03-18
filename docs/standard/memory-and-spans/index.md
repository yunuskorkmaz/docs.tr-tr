---
title: Bellek ve yayılma
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: b61b1dbbedf4658fe113986fbb4a792a2f574534
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121994"
---
# <a name="memory--and-span-related-types"></a><span data-ttu-id="d7f7e-102">Bellek ve yayılma ile ilgili türleri</span><span class="sxs-lookup"><span data-stu-id="d7f7e-102">Memory- and span-related types</span></span>

<span data-ttu-id="d7f7e-103">.NET Core 2.1 ile başlayarak,.NET, rasgele belleğin bitişik, güçlü bir şekilde yazılmış bölgesini temsil eden birbiriyle ilişkili bir dizi türü içerir.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-103">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly-typed region of arbitrary memory.</span></span> <span data-ttu-id="d7f7e-104">Bunlar:</span><span class="sxs-lookup"><span data-stu-id="d7f7e-104">These include:</span></span>

- <span data-ttu-id="d7f7e-105"><xref:System.Span%601?displayProperty=nameWithType>, bitişik bir bellek bölgesine erişmek için kullanılan bir tür.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-105"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="d7f7e-106">Bir <xref:System.Span%601> örnek `T`türü bir dizi tarafından desteklenebilir , a <xref:System.String>, [stackalloc](../../csharp/language-reference/operators/stackalloc.md)ile ayrılmış bir arabellek , ya da yönetilmeyen bellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-106">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="d7f7e-107">Yığına ayrılması gerektiği için, bir dizi kısıtlaması vardır.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-107">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="d7f7e-108">Örneğin, bir sınıftaki bir alan <xref:System.Span%601>türde olamaz ve asynchronous işlemlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-108">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="d7f7e-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, yapının <xref:System.Span%601> değişmez bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="d7f7e-110"><xref:System.Memory%601?displayProperty=nameWithType>, yığın yerine yönetilen yığına ayrılan bitişik bir bellek bölgesi.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-110"><xref:System.Memory%601?displayProperty=nameWithType>, a contiguous region of memory that is allocated on the managed heap rather than the stack.</span></span> <span data-ttu-id="d7f7e-111">Bir <xref:System.Memory%601> örnek, bir dizi tür `T` veya <xref:System.String>bir .</span><span class="sxs-lookup"><span data-stu-id="d7f7e-111">A <xref:System.Memory%601> instance can be backed by an array of type `T` or a <xref:System.String>.</span></span> <span data-ttu-id="d7f7e-112">Yönetilen yığında depolanabildiği için, <xref:System.Memory%601> .'ın hiçbir <xref:System.Span%601>sınırlaması yoktur.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-112">Because it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="d7f7e-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, yapının <xref:System.Memory%601> değişmez bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="d7f7e-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, bellek havuzundan bir sahibine güçlü bir şekilde yazılan bellek bloklarını ayırır.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly-typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="d7f7e-115"><xref:System.Buffers.IMemoryOwner%601>örnekleri arayarak <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> havuzdan kiralanabilir ve arayarak <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>havuza geri bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-115"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="d7f7e-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, bellek bloğunun sahibini temsil eder ve yaşam boyu yönetimini denetler.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="d7f7e-117"><xref:System.Buffers.MemoryManager%601>, güvenli tutamaçları gibi ek türler tarafından <xref:System.Memory%601> desteklenebilir şekilde <xref:System.Memory%601> uygulanması yerine kullanılabilecek soyut bir taban sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-117"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="d7f7e-118"><xref:System.Buffers.MemoryManager%601>gelişmiş senaryolar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-118"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="d7f7e-119"><xref:System.ArraySegment%601>, belirli bir dizinden başlayan belirli sayıda dizi öğesi için bir sarmalayıcı.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-119"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="d7f7e-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, dizeleri, dizileri ve dizi parçalarını bloklara dönüştürmek <xref:System.Memory%601> için uzantı yöntemleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="d7f7e-121">Önceki çerçeveler <xref:System.Span%601> için <xref:System.Memory%601> ve [System.Memory NuGet paketinde](https://www.nuget.org/packages/System.Memory/)mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-121">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="d7f7e-122">Daha fazla bilgi <xref:System.Buffers?displayProperty=nameWithType> için ad alanına bakın.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-122">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="d7f7e-123">Bellek ve yayılma alanı ile çalışma</span><span class="sxs-lookup"><span data-stu-id="d7f7e-123">Working with memory and span</span></span>

<span data-ttu-id="d7f7e-124">Bellek ve yayılmayla ilgili türler genellikle verileri bir işleme ardışık alanında depolamak için kullanıldığından, geliştiricilerin <xref:System.Span%601> <xref:System.Memory%601>, ve ilgili türleri kullanırken bir dizi en iyi uygulamaları izlemesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-124">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="d7f7e-125">Bu en iyi uygulamalar [Bellek\<T>\<ve Span T> kullanım yönergelerinde](memory-t-usage-guidelines.md)belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-125">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7f7e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-126">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
