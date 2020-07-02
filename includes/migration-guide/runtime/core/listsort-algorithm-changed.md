---
ms.openlocfilehash: 9dada93c3330331064b7a944d97d61edb4dea299
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620580"
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
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|
