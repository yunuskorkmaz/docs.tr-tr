---
title: Bellek ve yayılmalar
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: c60c08d27c0e41228a15e8acdf01a9af28a23762
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201965"
---
# <a name="memory--and-span-related-types"></a>Bellek ve yayılma ile ilgili türler

.NET Core 2,1 ' den itibaren, .NET, rastgele bellek içeren, bitişik ve kesin olarak belirlenmiş bir bölgeyi temsil eden bir dizi ilişkili tür içerir. Bu modüller şunlardır:

- <xref:System.Span%601?displayProperty=nameWithType>, belleğin bitişik bir bölgesine erişmek için kullanılan bir tür. Bir <xref:System.Span%601> örnek türünde bir dizi, `T` <xref:System.String> ,, [stackalloc](../../csharp/language-reference/operators/stackalloc.md)ile ayrılmış bir arabellek veya yönetilmeyen bellek işaretçisi tarafından yönetilebilir. Yığına ayrılması gerektiğinden, bir dizi kısıtlamaya sahiptir. Örneğin, bir sınıftaki bir alan türünde olamaz <xref:System.Span%601> , ya da zaman uyumsuz işlemlerde dağıtılabilir.

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, yapının sabit bir sürümüdür <xref:System.Span%601> .

- <xref:System.Memory%601?displayProperty=nameWithType>, yığın yerine yönetilen yığında ayrılan belleğin bitişik bir bölgesi. Bir <xref:System.Memory%601> örnek, veya türünde bir dizi tarafından yönetilebilir `T` <xref:System.String> . Yönetilen yığında depolanabileceğinden, <xref:System.Memory%601> kısıtlamaları yoktur <xref:System.Span%601> .

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, yapının sabit bir sürümüdür <xref:System.Memory%601> .

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, bellek havuzundan kesin olarak belirlenmiş bellek bloklarını Sahibe ayırır. <xref:System.Buffers.IMemoryOwner%601>örnekler, çağırarak havuzdan <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> geri dönerek yeniden kullanıma sunularak havuza eklenebilir <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType> .

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, bir bellek bloğunun sahibini temsil eder ve ömrü yönetimini denetler.

- <xref:System.Buffers.MemoryManager%601>, <xref:System.Memory%601> <xref:System.Memory%601> güvenli işleyiciler gibi ek türler tarafından desteklenen için uygulamasının yerini değiştirmek üzere kullanılabilecek bir soyut temel sınıf. <xref:System.Buffers.MemoryManager%601>, gelişmiş senaryolar için tasarlanmıştır.

- <xref:System.ArraySegment%601>, belirli bir dizinden başlayarak belirli sayıda dizi öğesi için sarmalayıcı.

- <xref:System.MemoryExtensions?displayProperty=nameWithType>, dizeler, diziler ve dizi segmentlerini bloklara dönüştürmek için uzantı yöntemleri koleksiyonu <xref:System.Memory%601> .

> [!NOTE]
> Daha önceki çerçeveler için <xref:System.Span%601> ve <xref:System.Memory%601> [System. Memory NuGet paketinde](https://www.nuget.org/packages/System.Memory/)kullanılabilir.

Daha fazla bilgi için bkz <xref:System.Buffers?displayProperty=nameWithType> . ad alanı.

## <a name="working-with-memory-and-span"></a>Bellek ve yayılma ile çalışma

Bellek ve yayılma ile ilgili türler genellikle verileri bir işlem ardışık düzeninde depolamak için kullanıldığından, geliştiricilerin <xref:System.Span%601> , <xref:System.Memory%601> ve ile ilgili türleri kullanırken en iyi yöntemler kümesini izlemesi önemlidir. Bu en iyi uygulamalar [bellek \<T> ve yayma \<T> Kullanım yönergeleri](memory-t-usage-guidelines.md)bölümünde belgelenmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
