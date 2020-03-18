---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901644"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a>MVC: "Pubternal" türleri dahili olarak değiştirildi

Core 3.0ASP.NET, MVC'deki tüm "pubternal" türleri `public` desteklenen bir ad `internal` alanında veya uygun şekilde güncelleştirildi.

#### <a name="change-description"></a>Açıklamayı değiştir

ASP.NET Core'da "pubternal" türleri `public` -suffixed `.Internal`ad alanında olduğu ancak ikamet ettiğini beyan eder. Bu tür `public`olmasına ne kadar , hiçbir destek ilkesi var ve kırılma değişikliklerine tabidir. Ne yazık ki, bu tür kazara kullanımı, bu projelerde değişiklikler kırma ve çerçeve korumak için yeteneği sınırlayan sonuçlanan yaygın olmuştur.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

MVC bazı türleri `public` ama `.Internal` bir ad alanı vardı. Bu tür hiçbir destek ilkesi vardı ve kırılma değişikliklere tabi idi.

#### <a name="new-behavior"></a>Yeni davranış

Tüm bu tür desteklenen `public` bir ad alanında olmak üzere `internal`güncelleştirilir veya .

#### <a name="reason-for-change"></a>Değişiklik nedeni

"Pubternal" türlerinin kazara kullanımı yaygın olmuştur, bu projelerde değişiklikler kırma ve çerçeve korumak için yeteneğini sınırlayan sonuçlanan.

#### <a name="recommended-action"></a>Önerilen eylem

Gerçekten `public` olmuş ve yeni, desteklenen bir ad alanına taşınmış türleri kullanıyorsanız, başvurularınızı yeni ad alanlarıyla eşleşecek şekilde güncelleyin.

Olarak işaretlenmiş türleri `internal`kullanıyorsanız, bir alternatif bulmanız gerekir. Daha önce "pubternal" türleri kamu kullanımı için desteklenmedi. Bu ad alanlarında uygulamalarınız için kritik öneme sahip belirli türler varsa, [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)adresinden bir sorun dosyalayın. İstenen tiplerin `public`yapılmasında dikkat edilmesi gereken hususlar göz önünde bulundurulabilir.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

Bu değişiklik, aşağıdaki ad alanlarındatürleri içerir:

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
