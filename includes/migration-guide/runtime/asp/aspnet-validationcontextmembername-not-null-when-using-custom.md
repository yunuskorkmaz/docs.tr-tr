---
ms.openlocfilehash: c0be08023f80bf0f96cc08f34b9ea8c5a73839e3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77466133"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>Özel Dataaçıklamalarda. ValidationAttribute kullanılırken ASP.NET ValidationContext. MemberName NULL değil

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ve önceki sürümlerde, özel bir <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>kullanılırken <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> özelliği `null`döndürür. 2019 Ekim 4,8 ' den önceki .NET Framework sürümünde üye adı döndürülür. .NET Framework 4,8 için [kalite toplamasının .NET Framework ekim 2019 önizlemesiyle](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) başlayarak, varsayılan olarak `null` döndürür ancak bunun yerine üye adını döndürmeyi tercih edebilirsiniz. |
|Öneri|Aşağıdaki ayarı, özelliği için *Web. config* dosyanıza, .NET Framework 4,8 ve sonraki sürümleri Için [.NET Framework Ekim 2019 ' de kalite toplamasının](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) , üye adını döndürecek şekilde ekleyin:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Güncelleştirme 2019 ' den önceki .NET Framework 4,8 sürümünde, bunu *Web. config* dosyanıza eklemek önceki davranışı geri yükler ve özellik `null`döndürür.|
|Kapsam|Bilinmiyor|
|Sürüm|4.8|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
