---
ms.openlocfilehash: 29908ed916690e67db3cc5d72ebe1b1c6aea45c6
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325205"
---
### <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a>IIS: URL yeniden yazma ara yazılımı sorgu dizeleri korunur

Bir IIS Urlyeniden yazma ara yazılım hatası sorgu dizesinin yeniden yazma kurallarında korunması engelledi. Bu hata, IIS Urlyeniden yazma modülünün davranışıyla tutarlılığı sağlamak için düzeltildi.

Tartışma için bkz. sorun [DotNet/aspnetcore # 22972](https://github.com/dotnet/aspnetcore/issues/22972).

#### <a name="version-introduced"></a>Sunulan sürüm

ASP.NET Core 5,0 Preview 7

#### <a name="old-behavior"></a>Eski davranış

Aşağıdaki yeniden yazma kuralını göz önünde bulundurun:

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

Önceki kural sorgu dizesini eklememez. Yerine öğesine yeniden yönlendirme gibi bir URI `/about?id=1` `/contact` `/contact?id=1` . `appendQueryString`Özniteliği `true` de varsayılan olarak olur.

#### <a name="new-behavior"></a>Yeni davranış

Sorgu dizesi korunur. [Eski davranıştaki](#old-behavior) örnekteki URI, olur `/contact?id=1` .

#### <a name="reason-for-change"></a>Değişiklik nedeni

Eski davranış IIS Urlyeniden yazma modülünün davranışıyla eşleşmedi. Ara yazılım ve modülle modül arasında taşıma desteği sağlamak için, amaç tutarlı davranışları korumaktır.

#### <a name="recommended-action"></a>Önerilen eylem

Sorgu dizesini kaldırma davranışı tercih edilirse, `action` öğesini olarak ayarlayın `appendQueryString="false"` .

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->
