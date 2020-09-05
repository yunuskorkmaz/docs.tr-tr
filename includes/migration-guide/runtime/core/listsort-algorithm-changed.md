---
ms.openlocfilehash: 09bd2c6312493f8b6369d05d8f1c4e88e4c05ece
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497804"
---
### <a name="listsort-algorithm-changed"></a>List. Sort algoritması değişti

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' den başlayarak, <xref:System.Collections.Generic.List%601?displayProperty=fullName> sıralama algoritması değişmiştir (bir hızlı sıralama yerine yönelik sıralaması olacak şekilde). <xref:System.Collections.Generic.List%601?displayProperty=fullName>sıralaması hiçbir zaman kararlı olmamıştır, ancak bu değişiklik farklı senaryolara karşı tutarlı şekilde sıralama yapılmasına neden olabilir. Bu, benzer öğelerin API 'nin sonraki çağrılarında farklı siparişlerde sıralabileceği anlamına gelir.

#### <a name="suggestion"></a>Öneri

Eski sıralama algoritması da kararsız olduğundan (biraz farklı yollarla), her zaman belirli bir sırada sıralama için eşdeğer öğelere bağlı bir kod olmamalıdır. Bu değere bağlı olan ve eski davranışa sahip olan kod örnekleri varsa, bu kod, öğeleri istenen sırada belirleyici olarak sıralayan bir karşılaştırıcı kullanmak için güncelleştirilmeleri gerekir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Geçirgen|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Generic.List`1.Sort``
- ``M:System.Collections.Generic.List`1.Sort(System.Collections.Generic.IComparer{`0})``
- ``M:System.Collections.Generic.List`1.Sort(System.Comparison{`0})``
- ``M:System.Collections.Generic.List`1.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{`0})``

-->
