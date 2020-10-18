---
ms.openlocfilehash: 1ddc2cea19872b44ff9659bcebd76117587ea89a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159501"
---
### <a name="targetframework-change-from-netcoreapp-to-net"></a>TargetFramework, netcoreapp 'ten net 'e değişiklik

MSBuild `TargetFramework` özelliğinin değeri iken `netcoreapp3.1` olarak değiştirildi `net5.0` . Bu, değerini ayrıştırmaya dayalı kodu kesebilir `TargetFramework` .

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 1,0-3,1 ' de, MSBuild `TargetFramework` özelliğinin değeri `netcoreapp` , örneğin `netcoreapp3.1` .NET Core 3,1 ' i hedefleyen uygulamalar için ile başlar. .NET 5,0 ' den başlayarak, bu değer .NET 5,0 için yalnızca ile başlamak üzere basitleştirilmiştir `net` `net5.0` .

Daha fazla bilgi için, [The future of .NET Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) [.NET 5 ' te .NET Standard ve hedef çerçeve adları](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md)bölümüne bakın.

#### <a name="reason-for-change"></a>Değişiklik nedeni

- Değeri basitleştirir `TargetFramework` .
- Projelerin özelliği içine içermesini sağlar `TargetPlatform` `TargetFramework` .

#### <a name="recommended-action"></a>Önerilen eylem

Değerini ayrıştırdığı mantığa sahipseniz `TargetFramework` güncelleştirmeniz gerekir. Örneğin, aşağıdaki MSBuild koşulu değerini kullanır `TargetFramework` .

```xml
<PropertyGroup Condition="$(TargetFramework.StartsWith('netcoreapp'))">
```

Bu gereksinim için kodu, hedef Framework tanımlayıcısını karşılaştırmak üzere güncelleştirebilirsiniz.

```xml
<PropertyGroup Condition="'$([MSBuild]::GetTargetFrameworkIdentifier('$(TargetFramework)'))' == '.NETCoreApp'">
```

#### <a name="category"></a>Kategori

MSBuild

#### <a name="affected-apis"></a>Etkilenen API’ler

YOK

<!--

#### Affected APIs

Not detectable via API analysis.

-->
