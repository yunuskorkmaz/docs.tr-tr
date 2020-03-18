---
ms.openlocfilehash: f6fd75c5b49156f44d31c650ea452eb549f13b0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901685"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC: JsonResult Microsoft.AspNetCore.Mvc.Core taşındı

`JsonResult`meclise `Microsoft.AspNetCore.Mvc.Core` taşındı. Bu tür [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json)tanımlanır için kullanılır. Bu sorunu kullanıcıların çoğunluğu için `Microsoft.AspNetCore.Mvc.Formatters.Json` gidermek için derleme düzeyinde [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) özniteliği eklendi. Üçüncü taraf kitaplıkları kullanan uygulamalar sorunlarla karşılaşabilir.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 6

#### <a name="old-behavior"></a>Eski davranış

2,2 tabanlı kitaplık kullanan bir uygulama başarıyla oluşturur.

#### <a name="new-behavior"></a>Yeni davranış

2.2 tabanlı kitaplık kullanan bir uygulama derlemede başarısız olur. Aşağıdaki metnin bir varyasyonunu içeren bir hata sağlanır:

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

Böyle bir sorun örneği için [dotnet/aspnetcore#7220'ye](https://github.com/dotnet/aspnetcore/issues/7220)bakın.

#### <a name="reason-for-change"></a>Değişiklik nedeni

[aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325)adresinde açıklandığı gibi ASP.NET Core bileşiminde platform düzeyinde değişiklikler.

#### <a name="recommended-action"></a>Önerilen eylem

2.2 sürümüne `Microsoft.AspNetCore.Mvc.Formatters.Json` karşı derlenen kitaplıkların tüm tüketiciler için sorunu çözmek için yeniden derlenmeleri gerekebilir. Etkilenirse, kitaplık yazarına başvurun. Core 3.0 ASP.NET hedeflemek için kitaplığın yeniden derlemisini isteyin.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
