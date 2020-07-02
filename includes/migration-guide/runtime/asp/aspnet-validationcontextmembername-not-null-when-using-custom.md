---
ms.openlocfilehash: 7002c74594993ac6bf28643ef3271da356190c66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622063"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>Özel Dataaçıklamalarda. ValidationAttribute kullanılırken ASP.NET ValidationContext. MemberName NULL değil

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.2 ve önceki sürümlerde, özel bir kullanırken <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> özelliği döndürür `null` . 2019 Ekim 4,8 ' den önceki .NET Framework sürümünde üye adı döndürülür. .NET Framework 4,8 için [kalite toplamasının .NET Framework ekim 2019 önizlemesiyle](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) başlayarak, `null` Varsayılan olarak döndürür, ancak bunun yerine üye adını döndürmeyi tercih edebilirsiniz.

#### <a name="suggestion"></a>Öneri

*web.config* dosyanıza, .NET Framework 4,8 ve sonraki sürümleri Için [.NET Framework Ekim 2019 Preview 'ın kalite toplamasının](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) üye adını döndürmesi için aşağıdaki ayarı ekleyin:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Güncelleştirme 2019 ' den önceki .NET Framework 4,8 sürümünde, bunu *web.config* dosyanıza eklemek önceki davranışı geri yükler ve özellik döndürür `null` .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Bilinmiyor|
|Sürüm|4,8|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
