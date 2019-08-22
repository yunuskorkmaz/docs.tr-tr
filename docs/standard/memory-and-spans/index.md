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
# <a name="memory--and-span-related-types"></a>Bellek ve yayılma ile ilgili türler

.NET Core 2,1 ' den itibaren, .NET, isteğe bağlı, kesin olarak belirlenmiş bir bellek bölgesini temsil eden bir dizi ilişkili tür içerir. Bu güncelleştirmeler şunlardır:

- <xref:System.Span%601?displayProperty=nameWithType>, belleğin bitişik bir bölgesine erişmek için kullanılan bir tür. Bir <xref:System.Span%601> örnek `T` türünde<xref:System.String>bir dizi,,, [stackalloc](../../csharp/language-reference/operators/stackalloc.md)ile ayrılmış bir arabellek veya yönetilmeyen bellek işaretçisi tarafından yönetilebilir. Yığına ayrılması gerektiğinden, bir dizi kısıtlamaya sahiptir. Örneğin, bir sınıftaki bir alan türünde <xref:System.Span%601>olamaz, ya da zaman uyumsuz işlemlerde dağıtılabilir.

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, <xref:System.Span%601> yapının sabit bir sürümüdür.

- <xref:System.Memory%601?displayProperty=nameWithType>, yığın yerine yönetilen yığında ayrılan belleğin bitişik bir bölgesi. Bir <xref:System.Memory%601> örnek, `T` veya<xref:System.String>türünde bir dizi tarafından yönetilebilir. Yönetilen yığında depolanabileceğinden, <xref:System.Memory%601> <xref:System.Span%601>kısıtlamaları yoktur.

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, <xref:System.Memory%601> yapının sabit bir sürümüdür.

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, bir bellek havuzundan bir sahibe kesin olarak belirlenmiş bellek blokları ayıran. <xref:System.Buffers.IMemoryOwner%601>örnekler, çağırarak havuzdan geri dönerek yeniden <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>kullanıma sunularak havuza eklenebilir.

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, bir bellek bloğunun sahibini temsil eder ve ömrü yönetimini denetler.

- <xref:System.Buffers.MemoryManager%601>, güvenli işleyiciler gibi ek türler tarafından desteklenen için uygulamasının <xref:System.Memory%601> <xref:System.Memory%601> yerini değiştirmek üzere kullanılabilecek bir soyut temel sınıf. <xref:System.Buffers.MemoryManager%601>, gelişmiş senaryolar için tasarlanmıştır.

- <xref:System.ArraySegment%601>, belirli bir dizinden başlayarak belirli sayıda dizi öğesi için sarmalayıcı.

- <xref:System.MemoryExtensions?displayProperty=nameWithType>, dizeler, diziler ve dizi segmentlerini <xref:System.Memory%601> bloklara dönüştürmek için uzantı yöntemleri koleksiyonu.

> [!NOTE]
> Daha önceki çerçeveler <xref:System.Span%601> için ve <xref:System.Memory%601> [System. Memory NuGet paketinde](https://www.nuget.org/packages/System.Memory/)kullanılabilir.

Daha fazla bilgi için bkz <xref:System.Buffers?displayProperty=nameWithType> . ad alanı.

## <a name="working-with-memory-and-span"></a>Bellek ve yayılma ile çalışma

Bellek ve yayılma ile ilgili türler genellikle verileri bir işlem ardışık düzeninde depolamak için kullanıldığından, geliştiricilerin, <xref:System.Span%601> <xref:System.Memory%601>ve ile ilgili türleri kullanırken en iyi yöntemler kümesini izlemesi önemlidir. Bu en iyi uygulamalar, [\<bellek t > ' de belgelenmiştir\<ve > Kullanım yönergeleri ' ne yayılamaz](memory-t-usage-guidelines.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
