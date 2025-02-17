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
# <a name="complexity-of-linq-orderbyfirstordefault-increased"></a>LINQ OrderBy 'in karmaşıklığı. Ilk {OrDefault} artırılmış

<xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> Ve uygulamaları <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> değişmiştir, işlem için daha fazla karmaşıklık elde edilir.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 1. x-3. x ' te, çağırarak <xref:System.Linq.Enumerable.OrderBy%2A> veya <xref:System.Linq.Enumerable.OrderByDescending%2A> takip eden ya da <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> `O(N)` karmaşıklıkla çalışan. Yalnızca First (veya default) öğesi gerekli olduğundan, bunu bulmak için yalnızca bir numaralandırma gereklidir. Ancak, veya için sağlanan koşul <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> tam olarak çağrılır `N` , burada `N` sıranın uzunluğudur.

.NET 5 ve sonraki sürümlerde, [](https://github.com/dotnet/runtime/pull/36643) <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.OrderByDescending%2A> <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> `O(N log N)` karmaşıklık yerine karmaşıklıkla `O(N)` veya onu çağıran ya da çalışan bir değişiklik yapılmıştır. Ancak, veya için sağlanan koşul, <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> genel performans için daha önemli olan veya *zamansız* olarak çağrılabilir `N` .

> [!NOTE]
> Bu değişiklik .NET Framework içindeki işlemin uygulanmasıyla ve karmaşıklığıyla eşleşir.

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu koşulda, .NET Core 1,0 ' de tanıtılan uygulama geri çevrildiğinden, koşulun daha az kez çağrılmasından faydalandı. Daha fazla bilgi için [Bu DotNet/Runtime sorununa](https://github.com/dotnet/runtime/issues/31554)bakın.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

Geliştirici bölümünde herhangi bir eylem gerekmez.

## <a name="affected-apis"></a>Etkilenen API’ler

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
