---
ms.openlocfilehash: 97fab784acac4331894547eea27fc21b485597fb
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366869"
---
### <a name="passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation"></a><span data-ttu-id="9aa05-101">GroupCollection 'ı IEnumerable alan genişletme yöntemlerine geçirme, \<T> Kesinleştirme gerektirir</span><span class="sxs-lookup"><span data-stu-id="9aa05-101">Passing GroupCollection to extension methods taking IEnumerable\<T> requires disambiguation</span></span>

<span data-ttu-id="9aa05-102">Bir üzerinde alan bir genişletme yöntemi çağrılırken `IEnumerable<T>` <xref:System.Text.RegularExpressions.GroupCollection> , türü bir cast kullanarak kesinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9aa05-102">When calling an extension method that takes an `IEnumerable<T>` on a <xref:System.Text.RegularExpressions.GroupCollection>, you must disambiguate the type using a cast.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9aa05-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="9aa05-103">Change description</span></span>

<span data-ttu-id="9aa05-104">.NET Core 3,0 ' den başlayarak <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> , `IEnumerable<KeyValuePair<String,Group>>` onun da dahil olduğu diğer türlere ek olarak uygular `IEnumerable<Group>` .</span><span class="sxs-lookup"><span data-stu-id="9aa05-104">Starting in .NET Core 3.0, <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> implements `IEnumerable<KeyValuePair<String,Group>>` in addition to the other types it implements, including `IEnumerable<Group>`.</span></span> <span data-ttu-id="9aa05-105">Bu, alan bir genişletme yöntemi çağrılırken belirsizliğe neden olur <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="9aa05-105">This results in ambiguity when calling an extension method that takes an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="9aa05-106">Örneğin, bu tür bir genişletme yöntemini bir örnek üzerinde çağırırsanız, <xref:System.Text.RegularExpressions.GroupCollection> Örneğin, <xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType> Aşağıdaki derleyici hatasını görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="9aa05-106">If you call such an extension method on a <xref:System.Text.RegularExpressions.GroupCollection> instance, for example, <xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType>, you'll see the following compiler error:</span></span>

<span data-ttu-id="9aa05-107">**CS1061: ' GroupCollection ', ' Count ' için bir tanım içermiyor ve ' GroupCollection ' türünde bir ilk bağımsız değişken kabul eden hiçbir erişilebilir genişletme metodu bulunamadı (bir using yönergeniz veya derleme başvurunuz eksik olabilir mi?)**</span><span class="sxs-lookup"><span data-stu-id="9aa05-107">**CS1061: 'GroupCollection' does not contain a definition for 'Count' and no accessible extension method 'Count' accepting a first argument of type 'GroupCollection' could be found (are you missing a using directive or an assembly reference?)**</span></span>

<span data-ttu-id="9aa05-108">Önceki .NET sürümlerinde hiçbir belirsizlik yoktu ve derleyici hatası yok.</span><span class="sxs-lookup"><span data-stu-id="9aa05-108">In previous versions of .NET, there was no ambiguity and no compiler error.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9aa05-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9aa05-109">Version introduced</span></span>

<span data-ttu-id="9aa05-110">3,0</span><span class="sxs-lookup"><span data-stu-id="9aa05-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9aa05-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="9aa05-111">Reason for change</span></span>

<span data-ttu-id="9aa05-112">Bu, [istemeden bir değişikliğe](https://github.com/dotnet/corefx/pull/30077)neden oldu.</span><span class="sxs-lookup"><span data-stu-id="9aa05-112">This was an [unintentional breaking change](https://github.com/dotnet/corefx/pull/30077).</span></span> <span data-ttu-id="9aa05-113">Bu bir süre içinde olduğu için, bu dosyayı döndürmeyi planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="9aa05-113">Because it has been like this for some time, we don't plan to revert it.</span></span> <span data-ttu-id="9aa05-114">Ayrıca, bu tür bir değişikliğin kendisi de kırılırdı.</span><span class="sxs-lookup"><span data-stu-id="9aa05-114">In addition, such a change would itself be breaking.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9aa05-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9aa05-115">Recommended action</span></span>

<span data-ttu-id="9aa05-116"><xref:System.Text.RegularExpressions.GroupCollection>Örnekler için, bir cast ile kabul eden genişletme yöntemlerine yapılan çağrıları belirsizliğini ortadan kaldırma `IEnumerable<T>` .</span><span class="sxs-lookup"><span data-stu-id="9aa05-116">For <xref:System.Text.RegularExpressions.GroupCollection> instances, disambiguate calls to extension methods that accept an `IEnumerable<T>` with a cast.</span></span>

```csharp
// Without a cast - causes CS1061.
match.Groups.Count(_ => true)

// With a disambiguating cast.
((IEnumerable<Group>)m.Groups).Count(_ => true);
```

#### <a name="category"></a><span data-ttu-id="9aa05-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="9aa05-117">Category</span></span>

<span data-ttu-id="9aa05-118">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="9aa05-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9aa05-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9aa05-119">Affected APIs</span></span>

<span data-ttu-id="9aa05-120">Kabul eden herhangi bir genişletme yöntemi <xref:System.Collections.Generic.IEnumerable%601> etkilenir.</span><span class="sxs-lookup"><span data-stu-id="9aa05-120">Any extension method that accepts an <xref:System.Collections.Generic.IEnumerable%601> is affected.</span></span> <span data-ttu-id="9aa05-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9aa05-121">For example:</span></span>

- <xref:System.Collections.Immutable.ImmutableArray.ToImmutableArray%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableList.ToImmutableList%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet%2A?displayProperty=fullName>
- <xref:System.Data.DataTableExtensions.CopyToDataTable%2A?displayProperty=fullName>
- <span data-ttu-id="9aa05-122">Yöntemlerin çoğu, `System.Linq.Enumerable` Örneğin, <xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9aa05-122">Most of the `System.Linq.Enumerable` methods, for example, <xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName></span></span>
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
