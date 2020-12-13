---
ms.openlocfilehash: 97fab784acac4331894547eea27fc21b485597fb
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366869"
---
### <a name="passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation"></a>GroupCollection 'ı IEnumerable alan genişletme yöntemlerine geçirme, \<T> Kesinleştirme gerektirir

Bir üzerinde alan bir genişletme yöntemi çağrılırken `IEnumerable<T>` <xref:System.Text.RegularExpressions.GroupCollection> , türü bir cast kullanarak kesinleştirmeniz gerekir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 ' den başlayarak <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> , `IEnumerable<KeyValuePair<String,Group>>` onun da dahil olduğu diğer türlere ek olarak uygular `IEnumerable<Group>` . Bu, alan bir genişletme yöntemi çağrılırken belirsizliğe neden olur <xref:System.Collections.Generic.IEnumerable%601> . Örneğin, bu tür bir genişletme yöntemini bir örnek üzerinde çağırırsanız, <xref:System.Text.RegularExpressions.GroupCollection> Örneğin, <xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType> Aşağıdaki derleyici hatasını görürsünüz:

**CS1061: ' GroupCollection ', ' Count ' için bir tanım içermiyor ve ' GroupCollection ' türünde bir ilk bağımsız değişken kabul eden hiçbir erişilebilir genişletme metodu bulunamadı (bir using yönergeniz veya derleme başvurunuz eksik olabilir mi?)**

Önceki .NET sürümlerinde hiçbir belirsizlik yoktu ve derleyici hatası yok.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu, [istemeden bir değişikliğe](https://github.com/dotnet/corefx/pull/30077)neden oldu. Bu bir süre içinde olduğu için, bu dosyayı döndürmeyi planlıyoruz. Ayrıca, bu tür bir değişikliğin kendisi de kırılırdı.

#### <a name="recommended-action"></a>Önerilen eylem

<xref:System.Text.RegularExpressions.GroupCollection>Örnekler için, bir cast ile kabul eden genişletme yöntemlerine yapılan çağrıları belirsizliğini ortadan kaldırma `IEnumerable<T>` .

```csharp
// Without a cast - causes CS1061.
match.Groups.Count(_ => true)

// With a disambiguating cast.
((IEnumerable<Group>)m.Groups).Count(_ => true);
```

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

Kabul eden herhangi bir genişletme yöntemi <xref:System.Collections.Generic.IEnumerable%601> etkilenir. Örneğin:

- <xref:System.Collections.Immutable.ImmutableArray.ToImmutableArray%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableList.ToImmutableList%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet%2A?displayProperty=fullName>
- <xref:System.Data.DataTableExtensions.CopyToDataTable%2A?displayProperty=fullName>
- Yöntemlerin çoğu, `System.Linq.Enumerable` Örneğin, <xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName>
- <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>

<!--

#### Affected APIs

- ``M:System.Collections.Immutable.ImmutableArray.ToImmutableArray``1(System.Collections.Generic.IEnumerable{``0})``
- `Overload:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary`
- `Overload:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet`
- ``M:System.Collections.Immutable.ImmutableList.ToImmutableList``1(System.Collections.Generic.IEnumerable{``0})``
- `Overload:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary`
- `Overload:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet`
- `Overload:System.Data.DataTableExtensions.CopyToDataTable`
- `Overload:System.Linq.Enumerable.Count`
- `Overload:System.Linq.ParallelEnumerable.AsParallel`
- `Overload:System.Linq.Queryable.AsQueryable`

-->
