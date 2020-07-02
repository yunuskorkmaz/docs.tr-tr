---
ms.openlocfilehash: 9131c91b34f4c24653dea37ea39af6be6e072287
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620633"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a>Sıralanabilir. boş &lt; TResult &gt; her zaman önbelleğe alınmış örnek döndürür

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' den başlayarak, <xref:System.Linq.Enumerable.Empty%60%601> her zaman önbelleğe alınmış bir iç örnek döndürür <xref:System.Collections.Generic.IEnumerable%601> . Daha önce, <xref:System.Linq.Enumerable.Empty%60%601> API çağrıldığında boş önbelleğe alma işlemi <xref:System.Collections.Generic.IEnumerable%601> yapılır, yani <xref:System.Linq.Enumerable.Empty%60%601> hızlı ve eşzamanlı olarak çağrılan bazı koşullarda, API 'ye yönelik farklı çağrılar için türün farklı örnekleri döndürülebilir.

#### <a name="suggestion"></a>Öneri

Önceki davranış belirleyici olmadığı için kodun bağımlı olması olası değildir. Ancak, boş numaralar karşılaştırılan ve bazen eşit olmayan bir şekilde bekleniyorsa, kullanmak yerine açık boş diziler oluşturulmalıdır ( <code>new T[0]</code> ) <xref:System.Linq.Enumerable.Empty%60%601> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|
