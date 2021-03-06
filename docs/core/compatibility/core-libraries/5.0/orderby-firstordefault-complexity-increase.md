---
title: "Son değişiklik: LINQ OrderBy 'in karmaşıklığı. Ilk {OrDefault} artırılmış"
description: OrderBy. First uygulamasının değiştiği çekirdek .NET kitaplıklarında .NET 5 ile ilgili son değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 4cd2dda5f60976f935505d6a6cb1e4c23d150d09
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257277"
---
# <a name="complexity-of-linq-orderbyfirstordefault-increased"></a><span data-ttu-id="5f07a-103">LINQ OrderBy 'in karmaşıklığı. Ilk {OrDefault} artırılmış</span><span class="sxs-lookup"><span data-stu-id="5f07a-103">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>

<span data-ttu-id="5f07a-104"><xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> Ve uygulamaları <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> değişmiştir, işlem için daha fazla karmaşıklık elde edilir.</span><span class="sxs-lookup"><span data-stu-id="5f07a-104">The implementation of <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> and <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> has changed, resulting in increased complexity for the operation.</span></span>

## <a name="change-description"></a><span data-ttu-id="5f07a-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="5f07a-105">Change description</span></span>

<span data-ttu-id="5f07a-106">.NET Core 1. x-3. x ' te, çağırarak <xref:System.Linq.Enumerable.OrderBy%2A> veya <xref:System.Linq.Enumerable.OrderByDescending%2A> takip eden ya da <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> `O(N)` karmaşıklıkla çalışan.</span><span class="sxs-lookup"><span data-stu-id="5f07a-106">In .NET Core 1.x - 3.x, calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N)` complexity.</span></span> <span data-ttu-id="5f07a-107">Yalnızca First (veya default) öğesi gerekli olduğundan, bunu bulmak için yalnızca bir numaralandırma gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5f07a-107">Since only the first (or default) element is required, only one enumeration is required to find it.</span></span> <span data-ttu-id="5f07a-108">Ancak, veya için sağlanan koşul <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> tam olarak çağrılır `N` , burada `N` sıranın uzunluğudur.</span><span class="sxs-lookup"><span data-stu-id="5f07a-108">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> is invoked exactly `N` times, where `N` is the length of the sequence.</span></span>

<span data-ttu-id="5f07a-109">.NET 5 ve sonraki sürümlerde, [](https://github.com/dotnet/runtime/pull/36643) <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.OrderByDescending%2A> <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> `O(N log N)` karmaşıklık yerine karmaşıklıkla `O(N)` veya onu çağıran ya da çalışan bir değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5f07a-109">In .NET 5 and later versions, a [change was made](https://github.com/dotnet/runtime/pull/36643) such that calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N log N)` complexity instead of `O(N)` complexity.</span></span> <span data-ttu-id="5f07a-110">Ancak, veya için sağlanan koşul, <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> genel performans için daha önemli olan veya *zamansız* olarak çağrılabilir `N` .</span><span class="sxs-lookup"><span data-stu-id="5f07a-110">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> may be invoked *less* than `N` times, which is more important for overall performance.</span></span>

> [!NOTE]
> <span data-ttu-id="5f07a-111">Bu değişiklik .NET Framework içindeki işlemin uygulanmasıyla ve karmaşıklığıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5f07a-111">This change matches the implementation and complexity of the operation in .NET Framework.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="5f07a-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="5f07a-112">Reason for change</span></span>

<span data-ttu-id="5f07a-113">Bu koşulda, .NET Core 1,0 ' de tanıtılan uygulama geri çevrildiğinden, koşulun daha az kez çağrılmasından faydalandı.</span><span class="sxs-lookup"><span data-stu-id="5f07a-113">The benefit of invoking the predicate fewer times outweighs a lower overall complexity, so the implementation that was introduced in .NET Core 1.0 was reverted.</span></span> <span data-ttu-id="5f07a-114">Daha fazla bilgi için [Bu DotNet/Runtime sorununa](https://github.com/dotnet/runtime/issues/31554)bakın.</span><span class="sxs-lookup"><span data-stu-id="5f07a-114">For more information, see [this dotnet/runtime issue](https://github.com/dotnet/runtime/issues/31554).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="5f07a-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f07a-115">Version introduced</span></span>

<span data-ttu-id="5f07a-116">5.0</span><span class="sxs-lookup"><span data-stu-id="5f07a-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="5f07a-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="5f07a-117">Recommended action</span></span>

<span data-ttu-id="5f07a-118">Geliştirici bölümünde herhangi bir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5f07a-118">No action is required on the developer's part.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="5f07a-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5f07a-119">Affected APIs</span></span>

- <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>
- <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Linq.Enumerable.OrderBy`
- `Overload:System.Linq.Enumerable.OrderByDescending`
- `M:System.Linq.Enumerable.First``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`
- `M:System.Linq.Enumerable.FirstOrDefault``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`

-->
