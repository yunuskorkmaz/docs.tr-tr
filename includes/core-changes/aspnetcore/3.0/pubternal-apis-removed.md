---
ms.openlocfilehash: 224cd3c7897c64ef05baba7d3d31dbe5ac0dd610
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606264"
---
### <a name="pubternal-apis-removed"></a>"Pubternal" API 'Leri kaldırıldı

ASP.NET Core ortak API yüzeyini daha iyi korumak için `*.Internal` ad alanları (API 'ler olarak adlandırılır) içindeki türlerin çoğu :::no-loc text="\"pubternal\""::: gerçekten dahili hale gelir. Bu ad alanlarındaki üyelerin herkese açık API 'Ler olarak desteklenmemesi hiç değildir. API 'Ler küçük sürümlerde kesilebilir ve genellikle olur. 3,0 ASP.NET Core güncelleştirme sırasında bu API 'Lere bağlı olan kod kesilir.

Daha fazla bilgi için bkz. [DotNet/aspnetcore # 4932](https://github.com/dotnet/aspnetcore/issues/4932) and [DotNet/aspnetcore # 11312](https://github.com/dotnet/aspnetcore/issues/11312).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

Etkilenen API 'Ler `public` erişim değiştiricisiyle işaretlenir ve `*.Internal` ad alanlarında bulunur.

#### <a name="new-behavior"></a>Yeni davranış

Etkilenen API 'Ler [iç](../../../../docs/csharp/language-reference/keywords/internal.md) erişim değiştiricisiyle işaretlenir ve artık bu derleme dışındaki kod tarafından kullanılamaz.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu API 'ler için rehberlik şu :::no-loc text="\"pubternal\""::: şekilde yapılır:

* Bildirimde bulunulmadan değişebilir.
* Son değişiklikleri engellemek için .NET ilkelerine tabi değildir.

API 'lerden çıkmak `public` ( `*.Internal` ad alanlarında bile) müşteriler için kafa karıştırıcı.

#### <a name="recommended-action"></a>Önerilen eylem

Bu :::no-loc text="\"pubternal\""::: API 'leri kullanmayı durdurun. Alternatif API 'Ler hakkında sorularınız varsa, [DotNet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) deposunda bir sorun açın.

Örneğin, bir ASP.NET Core 2,2 projesinde aşağıdaki HTTP isteği arabelleğe alma kodunu göz önünde bulundurun. `EnableRewind`Uzantı yöntemi `Microsoft.AspNetCore.Http.Internal` ad alanında bulunur.

```csharp
HttpContext.Request.EnableRewind();
```

ASP.NET Core 3,0 projesinde, `EnableRewind` çağrısını uzantı yöntemine yönelik bir çağrı ile değiştirin `EnableBuffering` . İstek arabelleğe alma özelliği geçmişte olduğu gibi çalışmaktadır. `EnableBuffering` Şimdi `internal` API 'yi çağırır.

```csharp
HttpContext.Request.EnableBuffering();
```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

`Microsoft.AspNetCore.*` `Microsoft.Extensions.*` Ad alanı adında bir kesimi olan ve ad alanındaki tüm API 'ler `Internal` . Örnek:

- `Microsoft.AspNetCore.Authentication.Internal`
- `Microsoft.AspNetCore.Builder.Internal`
- `Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `Microsoft.AspNetCore.DataProtection.Internal`
- `Microsoft.AspNetCore.Hosting.Internal`
- `Microsoft.AspNetCore.Http.Internal`
- `Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `Microsoft.AspNetCore.Mvc.Core.Internal`
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
- `Microsoft.AspNetCore.Rewrite.Internal`
- `Microsoft.AspNetCore.Routing.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Internal`
- `N:Microsoft.AspNetCore.Builder.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Internal`
- `N:Microsoft.AspNetCore.Hosting.Internal`
- `N:Microsoft.AspNetCore.Http.Internal`
- `N:Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `N:Microsoft.AspNetCore.Mvc.Core.Internal`
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
- `N:Microsoft.AspNetCore.Rewrite.Internal`
- `N:Microsoft.AspNetCore.Routing.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `N:Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

-->
