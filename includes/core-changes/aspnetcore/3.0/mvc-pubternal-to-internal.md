---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032835"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a>MVC: "Pubternal" türleri iç olarak değiştirildi

ASP.NET Core 3,0 ' de, MVC içindeki tüm "pubternal" türleri `public` desteklenen bir ad alanında ya da uygun şekilde güncelleştirildi `internal` .

#### <a name="change-description"></a>Açıklamayı Değiştir

ASP.NET Core, "pubternal" türleri olarak belirtilir, `public` ancak bir `.Internal` -sonsabit ad alanında bulunur. Bu türler olsa `public` da, destek ilkesi yoktur ve bu değişiklikler önemli değişikliklere tabidir. Ne yazık ki, bu türlerin yanlışlıkla kullanılması yaygındır ve bu projelerde oluşan değişikliklere neden olacak ve Framework 'ün bakımını yapma yeteneğini sınırlandırmıştır.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

MVC içindeki bazı türler `public` , ancak bir `.Internal` ad alanında. Bu türlerin destek ilkesi yoktu ve değişiklikler ortadan kaldırıldı.

#### <a name="new-behavior"></a>Yeni davranış

Bu tür türler desteklenen bir ad alanında olacak şekilde güncelleştirilir `public` veya olarak işaretlenir `internal` .

#### <a name="reason-for-change"></a>Değişiklik nedeni

"Pubternal" türlerinin yanlışlıkla kullanılması yaygındır ve bu projelerde oluşan değişikliklere neden olacak ve Framework 'ün bakımını yapma yeteneğini sınırlandırmıştır.

#### <a name="recommended-action"></a>Önerilen eylem

Gerçekten olan `public` ve yeni ve desteklenen bir ad alanına taşınan türler kullanıyorsanız, başvurularınızı yeni ad alanlarıyla eşleşecek şekilde güncelleştirin.

Olarak işaretlenen türler kullanıyorsanız `internal` , alternatif bulmanız gerekir. Daha önce "pubternal" türleri genel kullanım için hiçbir şekilde desteklenmez. Bu ad alanlarında uygulamalarınız için kritik olan belirli türler varsa, [DotNet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)' da bir sorun yapın. İstenen türleri oluşturmak için dikkat edilmesi gereken noktalar `public` .

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
