---
title: "Son değişiklik: TargetFramework, netcoreapp 'ten net 'e değiştirildi"
description: .NET 5 ' teki son değişiklik hakkında bilgi edinin ve MSBuild TargetFramework özelliğinin değeri netcoreapp 3.1'den net 5.0'da değiştirilmiştir.
ms.date: 10/17/2020
ms.openlocfilehash: 88bfe7602c83f61b56f11c4e0336702571369e3c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256497"
---
# <a name="targetframework-change-from-netcoreapp-to-net"></a>netcoreapp olan TargetFramework net olarak değiştirildi

MSBuild `TargetFramework` özelliğinin değeri iken `netcoreapp3.1` olarak değiştirildi `net5.0` . Bu, değerini ayrıştırmaya dayalı kodu kesebilir `TargetFramework` .

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 1,0-3,1 ' de, MSBuild `TargetFramework` özelliğinin değeri `netcoreapp` , örneğin `netcoreapp3.1` .NET Core 3,1 ' i hedefleyen uygulamalar için ile başlar. .NET 5 ' den itibaren bu değer, .NET 5,0 için yalnızca ile başlamak üzere basitleştirilmiştir `net` `net5.0` .

Daha fazla bilgi için, [](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) [.NET 5 ' te .NET Standard ve hedef çerçeve adları](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md)bölümüne bakın.

## <a name="reason-for-change"></a>Değişiklik nedeni

- Değeri basitleştirir `TargetFramework` .
- Projelerin özelliği içine içermesini sağlar `TargetPlatform` `TargetFramework` .

## <a name="recommended-action"></a>Önerilen eylem

Değerini ayrıştırdığı mantığa sahipseniz `TargetFramework` güncelleştirmeniz gerekir. Örneğin, aşağıdaki MSBuild koşulu değerini kullanır `TargetFramework` .

```xml
<PropertyGroup Condition="$(TargetFramework.StartsWith('netcoreapp'))">
```

Bu gereksinim için kodu, hedef Framework tanımlayıcısını karşılaştırmak üzere güncelleştirebilirsiniz.

```xml
<PropertyGroup Condition="'$([MSBuild]::GetTargetFrameworkIdentifier('$(TargetFramework)'))' == '.NETCoreApp'">
```

## <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
