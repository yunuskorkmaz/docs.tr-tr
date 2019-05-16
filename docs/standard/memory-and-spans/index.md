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
ms.openlocfilehash: 76a5c32660c8a08ef34c40f8f4ee9430e5ead5c8
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644285"
---
# <a name="memory--and-span-related-types"></a>Bellek ve aralık ilgili türler

.NET, .NET Core 2.1 ile başlayarak, bir dizi bitişik, kesin türü belirtilmiş rastgele bir bellek bölgesini temsil eden birbiriyle türlerini içerir. Bu güncelleştirmeler şunlardır:

- <xref:System.Span%601?displayProperty=nameWithType>, bitişik bellek bölgesini erişmek için kullanılan bir tür. A <xref:System.Span%601> örneği bir dizi türü tarafından desteklenen `T`, <xref:System.String>, arabellek ile ayrılan [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md), veya yönetilmeyen bellek işaretçisi. Yığında ayrılacak olduğundan, bazı kısıtlamalar vardır. Örneğin, bir alanın bir sınıf türünde olamaz <xref:System.Span%601>, ne de aralık içinde zaman uyumsuz işlemleri kullanılabilir.

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, sabit bir sürümünü <xref:System.Span%601> yapısı.

- <xref:System.Memory%601?displayProperty=nameWithType>, bölgesine bitişik bir yığın yerine yönetilen yığında ayrılan bellek. A <xref:System.Memory%601> örneği bir dizi türü tarafından desteklenen `T` veya <xref:System.String>. Yönetilen yığında depolanmış çünkü <xref:System.Memory%601> sınırlamaları hiçbirinin <xref:System.Span%601>.

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, sabit bir sürümünü <xref:System.Memory%601> yapısı.

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, hangi ayırır bellek blokları kesin türü belirtilmiş bir bellek havuzundan sahip. <xref:System.Buffers.IMemoryOwner%601> örnekleri gibi verilere dayanarak havuzdan çağırarak <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> ve geri çağırarak havuzuna serbest <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, bir bellek bloğu sahibi temsil eder ve kendi ömrü Yönetimi denetler.

- <xref:System.Buffers.MemoryManager%601>, uygulamasını değiştirmek için kullanılan bir soyut temel sınıf <xref:System.Memory%601> böylece <xref:System.Memory%601> güvenli tanıtıcıları gibi ek türleri tarafından desteklenir. <xref:System.Buffers.MemoryManager%601> Gelişmiş senaryolar için tasarlanmıştır.

- <xref:System.ArraySegment%601>, belirli bir dizinden başlayarak bir dizi öğeleri belirli bir dizi için bir sarmalayıcı.

- <xref:System.MemoryExtensions?displayProperty=nameWithType>, dizeler, diziler ve dizi segmentlere dönüştürmek için genişletme yöntemleri koleksiyonunu <xref:System.Memory%601> engeller.

> [!NOTE]
> Önceki çerçeveler için <xref:System.Span%601> ve <xref:System.Memory%601> kullanılabilir [System.Memory NuGet paketi](https://www.nuget.org/packages/System.Memory/).

Daha fazla bilgi için <xref:System.Buffers?displayProperty=nameWithType> ad alanı.

## <a name="working-with-memory-and-span"></a>Bellek ve yayılma ile çalışma

Bellek ve aralık ilgili türler genellikle bir işleme işlem hattı, verileri depolamak için kullanıldığından, geliştiriciler kullanırken birtakım en iyi uygulamaları izlemeniz önemlidir <xref:System.Span%601>, <xref:System.Memory%601>ve ilgili türler. Bu en iyi belgelenmiştir [bellek\<T > ve aralık\<T > kullanım yönergeleri](memory-t-usage-guidelines.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
