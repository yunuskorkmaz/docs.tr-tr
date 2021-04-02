---
title: '.NET 6 Son değişiklik: LINQ Queryable yöntemlerinin ek aşırı yüklemeleri'
description: System. Linq. Queryable türüne ek yöntem aşırı yüklemelerinin eklendiği çekirdek .NET kitaplıklarında .NET 6 ' dan fazla değişiklik hakkında bilgi edinin.
ms.date: 03/31/2021
ms.openlocfilehash: 15a4e480f7d1b4e110084e736fc920a522439e69
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106123578"
---
# <a name="new-systemlinqqueryable-method-overloads"></a>Yeni System. LINQ. Queryable yöntemi aşırı yüklemeleri

<xref:System.Linq.Queryable?displayProperty=fullName>' De uygulanan yeni özelliklerin bir parçası olarak ' ye ek ortak yöntem aşırı yüklemeleri eklenmiştir <https://github.com/dotnet/runtime/pull/47231> . Yöntemleri ararken yansıma kodunuz yeterince sağlam değilse, bu eklemeler sorgu sağlayıcısı uygulamalarınızı bozabilir.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 6 ' da, [etkilenen API 'ler](#affected-apis) bölümünde listelenen yöntemlere yeni aşırı yüklemeler eklenmiştir. Aşağıdaki örnekte gösterildiği gibi yansıma kodu, bu eklemelerin sonucu olarak kesilebilir:

```csharp
typeof(System.Linq.Queryable)
    .GetMethods(BindingFlags.Public | BindingFlags.Static)
    .Where(m => m.Name == "ElementAt")
    .Single();
```

Bu yansıma kodu artık <xref:System.InvalidOperationException> Şuna benzer bir ileti oluşturacak: **sıra birden fazla öğe içeriyor**.

## <a name="version-introduced"></a>Sunulan sürüm

6,0 Preview 3 ve Preview 4

## <a name="reason-for-change"></a>Değişiklik nedeni

LINQ API 'yi genişletmek için yeni aşırı yüklemeler eklenmiştir `Queryable` .

## <a name="recommended-action"></a>Önerilen eylem

Sorgu sağlayıcı kitaplığı yazarsıysanız, yansıma kodunuzun aşırı yük eklemeleri için dayanıklı olduğundan emin olun. Örneğin, <xref:System.Type.GetMethod%2A?displayProperty=nameWithType> yöntemin parametre türlerini açıkça kabul eden bir aşırı yükleme kullanın.

## <a name="affected-apis"></a>Etkilenen API’ler

Aşağıdaki genişletme yöntemleri için yeni aşırı yüklemeler eklendi <xref:System.Linq.Queryable> :

- <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Min%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Max%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Zip%2A?displayProperty=fullName>

<!--

### Category

- Core .NET libraries
- LINQ

### Affected APIs

- `Overload:System.Linq.Queryable.ElementAt`
- `Overload:System.Linq.Queryable.ElementAtOrDefault`
- `Overload:System.Linq.Queryable.Take`
- `Overload:System.Linq.Queryable.Min`
- `Overload:System.Linq.Queryable.Max`
- `Overload:System.Linq.Queryable.FirstOrDefault`
- `Overload:System.Linq.Queryable.LastOrDefault`
- `Overload:System.Linq.Queryable.SingleOrDefault`
- `Overload:System.Linq.Queryable.Zip`

-->
