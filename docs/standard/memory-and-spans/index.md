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
# <a name="memory--and-span-related-types"></a>Bellek ve yayılma ile ilgili türleri

.NET Core 2.1 ile başlayarak,.NET, rasgele belleğin bitişik, güçlü bir şekilde yazılmış bölgesini temsil eden birbiriyle ilişkili bir dizi türü içerir. Bunlar:

- <xref:System.Span%601?displayProperty=nameWithType>, bitişik bir bellek bölgesine erişmek için kullanılan bir tür. Bir <xref:System.Span%601> örnek `T`türü bir dizi tarafından desteklenebilir , a <xref:System.String>, [stackalloc](../../csharp/language-reference/operators/stackalloc.md)ile ayrılmış bir arabellek , ya da yönetilmeyen bellek için bir işaretçi. Yığına ayrılması gerektiği için, bir dizi kısıtlaması vardır. Örneğin, bir sınıftaki bir alan <xref:System.Span%601>türde olamaz ve asynchronous işlemlerinde kullanılabilir.

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, yapının <xref:System.Span%601> değişmez bir sürümü.

- <xref:System.Memory%601?displayProperty=nameWithType>, yığın yerine yönetilen yığına ayrılan bitişik bir bellek bölgesi. Bir <xref:System.Memory%601> örnek, bir dizi tür `T` veya <xref:System.String>bir . Yönetilen yığında depolanabildiği için, <xref:System.Memory%601> .'ın hiçbir <xref:System.Span%601>sınırlaması yoktur.

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, yapının <xref:System.Memory%601> değişmez bir sürümü.

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, bellek havuzundan bir sahibine güçlü bir şekilde yazılan bellek bloklarını ayırır. <xref:System.Buffers.IMemoryOwner%601>örnekleri arayarak <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> havuzdan kiralanabilir ve arayarak <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>havuza geri bırakılabilir.

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, bellek bloğunun sahibini temsil eder ve yaşam boyu yönetimini denetler.

- <xref:System.Buffers.MemoryManager%601>, güvenli tutamaçları gibi ek türler tarafından <xref:System.Memory%601> desteklenebilir şekilde <xref:System.Memory%601> uygulanması yerine kullanılabilecek soyut bir taban sınıfı. <xref:System.Buffers.MemoryManager%601>gelişmiş senaryolar için tasarlanmıştır.

- <xref:System.ArraySegment%601>, belirli bir dizinden başlayan belirli sayıda dizi öğesi için bir sarmalayıcı.

- <xref:System.MemoryExtensions?displayProperty=nameWithType>, dizeleri, dizileri ve dizi parçalarını bloklara dönüştürmek <xref:System.Memory%601> için uzantı yöntemleri koleksiyonu.

> [!NOTE]
> Önceki çerçeveler <xref:System.Span%601> için <xref:System.Memory%601> ve [System.Memory NuGet paketinde](https://www.nuget.org/packages/System.Memory/)mevcuttur.

Daha fazla bilgi <xref:System.Buffers?displayProperty=nameWithType> için ad alanına bakın.

## <a name="working-with-memory-and-span"></a>Bellek ve yayılma alanı ile çalışma

Bellek ve yayılmayla ilgili türler genellikle verileri bir işleme ardışık alanında depolamak için kullanıldığından, geliştiricilerin <xref:System.Span%601> <xref:System.Memory%601>, ve ilgili türleri kullanırken bir dizi en iyi uygulamaları izlemesi önemlidir. Bu en iyi uygulamalar [Bellek\<T>\<ve Span T> kullanım yönergelerinde](memory-t-usage-guidelines.md)belgelenmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
