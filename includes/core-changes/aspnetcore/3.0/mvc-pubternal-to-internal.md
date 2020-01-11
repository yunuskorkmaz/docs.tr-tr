---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901644"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a>MVC: "Pubternal" türleri iç olarak değiştirildi

ASP.NET Core 3,0 ' de, MVC içindeki tüm "pubternal" türleri desteklenen bir ad alanında `public` olacak şekilde veya `internal` uygun şekilde güncelleştirildi.

#### <a name="change-description"></a>Açıklamayı Değiştir

ASP.NET Core, "pubternal" türleri `public` olarak belirtilir, ancak bir `.Internal`soneki sabit ad alanında yer alır. Bu türler `public`olsa da, destek ilkesi yoktur ve değişiklikler önemli değişikliklere tabidir. Ne yazık ki, bu türlerin yanlışlıkla kullanılması yaygındır ve bu projelerde oluşan değişikliklere neden olacak ve Framework 'ün bakımını yapma yeteneğini sınırlandırmıştır.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

MVC içindeki bazı türler `public`, ancak bir `.Internal` ad alanında. Bu türlerin destek ilkesi yoktu ve değişiklikler ortadan kaldırıldı.

#### <a name="new-behavior"></a>Yeni davranış

Bu tür türler desteklenen bir ad alanında `public` ya da `internal`olarak işaretlenen şekilde güncelleştirilir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

"Pubternal" türlerinin yanlışlıkla kullanılması yaygındır ve bu projelerde oluşan değişikliklere neden olacak ve Framework 'ün bakımını yapma yeteneğini sınırlandırmıştır.

#### <a name="recommended-action"></a>Önerilen eylem

Gerçekten `public` olan ve yeni, desteklenen bir ad alanına taşınan türler kullanıyorsanız, başvurularınızı yeni ad alanlarıyla eşleşecek şekilde güncelleştirin.

`internal`olarak işaretlenen türler kullanıyorsanız, alternatif bulmanız gerekir. Daha önce "pubternal" türleri genel kullanım için hiçbir şekilde desteklenmez. Bu ad alanlarında uygulamalarınız için kritik olan belirli türler varsa, [DotNet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)' da bir sorun yapın. İstenen türlerin `public`yapılması için dikkat edilmesi gereken noktalar olabilir.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Bu değişiklik aşağıdaki ad alanları türlerini içerir:

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->
