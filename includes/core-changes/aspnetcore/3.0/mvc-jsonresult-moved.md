---
ms.openlocfilehash: 1356f3eee5e2d8090d7d96aafc07a19507a1aff1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721013"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC: JsonResult, Microsoft. AspNetCore. Mvc. Core 'a taşındı

`JsonResult`, `Microsoft.AspNetCore.Mvc.Core` derlemeye taşındı. Bu tür, [Microsoft. AspNetCore. Mvc. Formatters. JSON](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json)içinde tanımlanması için kullanılır. Bir derleme düzeyi [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) özniteliği, ' ye `Microsoft.AspNetCore.Mvc.Formatters.Json` , kullanıcıların çoğunluğunda bu sorunu gidermek için eklenmiştir. Üçüncü taraf kitaplıklar kullanan uygulamalar sorunlarla karşılaşabilir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 6

#### <a name="old-behavior"></a>Eski davranış

2,2 tabanlı kitaplık kullanan bir uygulama başarıyla oluşturulur.

#### <a name="new-behavior"></a>Yeni davranış

2,2 tabanlı kitaplık kullanan bir uygulama derleme hatası verir. Aşağıdaki metnin bir varyasyonunu içeren bir hata verilmiştir:

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

Bu tür bir sorunun örneği için bkz. [DotNet/aspnetcore # 7220](https://github.com/dotnet/aspnetcore/issues/7220).

#### <a name="reason-for-change"></a>Değişiklik nedeni

ASP.NET Core, [ASPNET/Duyurular # 325](https://github.com/aspnet/Announcements/issues/325)bölümünde açıklandığı gibi bileşim düzeyinde değişir.

#### <a name="recommended-action"></a>Önerilen eylem

2,2 sürümüne karşı derlenen kitaplıkların, `Microsoft.AspNetCore.Mvc.Formatters.Json` tüm tüketiciler için sorunu gidermek üzere yeniden derlenmesi gerekebilir. Etkileniyorsa kitaplık yazarına başvurun. ASP.NET Core 3,0 ' i hedeflemek için kitaplığın yeniden derlenmesi isteği.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
