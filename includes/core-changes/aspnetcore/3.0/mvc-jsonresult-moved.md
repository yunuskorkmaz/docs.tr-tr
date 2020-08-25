---
ms.openlocfilehash: 96c2a32dd7cca91e965601d715bbd4625bba439a
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811291"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC: JsonResult, Microsoft. AspNetCore. Mvc. Core 'a taşındı

`JsonResult` , `Microsoft.AspNetCore.Mvc.Core` derlemeye taşındı. Bu tür [ üzerindeMicrosoft.AspNetCore.Mvc.Formatters.Js](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json)tanımlanması için kullanılır. Bir derleme düzeyi [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) özniteliği, ' ye `Microsoft.AspNetCore.Mvc.Formatters.Json` , kullanıcıların çoğunluğunda bu sorunu gidermek için eklenmiştir. Üçüncü taraf kitaplıklar kullanan uygulamalar sorunlarla karşılaşabilir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 6

#### <a name="old-behavior"></a>Eski davranış

2,2 tabanlı kitaplık kullanan bir uygulama başarıyla oluşturulur.

#### <a name="new-behavior"></a>Yeni davranış

2,2 tabanlı kitaplık kullanan bir uygulama derleme hatası verir. Aşağıdaki metnin bir varyasyonunu içeren bir hata verilmiştir:

```output
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
