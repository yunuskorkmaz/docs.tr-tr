---
title: Bellek ve yayılmalar
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: b61b1dbbedf4658fe113986fbb4a792a2f574534
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121994"
---
# <a name="memory--and-span-related-types"></a>Bellek ve yayılma ile ilgili türler

.NET Core 2,1 ' den itibaren, .NET, isteğe bağlı, kesin olarak belirlenmiş bir bellek bölgesini temsil eden bir dizi ilişkili tür içerir. Bu güncelleştirmeler şunlardır:

- <xref:System.Span%601?displayProperty=nameWithType>, belleğin bitişik bir bölgesine erişmek için kullanılan bir tür. Bir <xref:System.Span%601> örnek, `T`, <xref:System.String>, [stackalloc](../../csharp/language-reference/operators/stackalloc.md)ile ayrılmış bir arabellek veya yönetilmeyen bellek işaretçisi tarafından desteklenen bir dizi tarafından yönetilebilir. Yığına ayrılması gerektiğinden, bir dizi kısıtlamaya sahiptir. Örneğin, bir sınıftaki alan <xref:System.Span%601>türünde olamaz, ya da zaman uyumsuz işlemlerde dağıtılabilir.

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, <xref:System.Span%601> yapısının sabit bir sürümüdür.

- yığın yerine yönetilen yığında ayrılan belleğin bitişik bir bölgesi olan <xref:System.Memory%601?displayProperty=nameWithType>. Bir <xref:System.Memory%601> örneği `T` veya <xref:System.String>türünde bir dizi tarafından yönetilebilir. Yönetilen yığında depolanabileceğinden, <xref:System.Memory%601> <xref:System.Span%601>hiçbir kısıtlama yoktur.

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, <xref:System.Memory%601> yapısının sabit bir sürümüdür.

- bir bellek havuzundan bir sahibe kesin olarak belirlenmiş bellek blokları ayıran <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>. <xref:System.Buffers.IMemoryOwner%601> örnekleri, <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> çağırarak ve <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>çağırarak havuza geri yayınlanan havuzdan yeniden dağıtılabilir.

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, bir bellek bloğunun sahibini temsil eder ve ömrü yönetimini denetler.

- <xref:System.Buffers.MemoryManager%601>, <xref:System.Memory%601> <xref:System.Memory%601> uygulanmasını değiştirmek için kullanılabilen, güvenli işleyiciler gibi ek türler tarafından desteklenen bir soyut temel sınıftır. <xref:System.Buffers.MemoryManager%601> gelişmiş senaryolara yöneliktir.

- belirli bir dizinden başlayarak belirli sayıda dizi öğesi için bir sarmalayıcı <xref:System.ArraySegment%601>.

- dize, dizi ve dizi segmentlerini <xref:System.Memory%601> bloklara dönüştürmek için uzantı yöntemleri koleksiyonu <xref:System.MemoryExtensions?displayProperty=nameWithType>.

> [!NOTE]
> Daha önceki çerçeveler için, [System. Memory NuGet paketinde](https://www.nuget.org/packages/System.Memory/)<xref:System.Span%601> ve <xref:System.Memory%601> kullanılabilir.

Daha fazla bilgi için <xref:System.Buffers?displayProperty=nameWithType> ad alanına bakın.

## <a name="working-with-memory-and-span"></a>Bellek ve yayılma ile çalışma

Bellek ve yayılma ile ilgili türler genellikle verileri bir işlem ardışık düzeninde depolamak için kullanıldığından, geliştiricilerin <xref:System.Span%601>, <xref:System.Memory%601>ve ilgili türleri kullanırken en iyi yöntemler kümesini izlemesi önemlidir. Bu en iyi uygulamalar, [bellek\<t > ve\<t > kullanım yönergelerine](memory-t-usage-guidelines.md)göre belgelenmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
