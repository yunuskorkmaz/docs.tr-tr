---
ms.openlocfilehash: c0be08023f80bf0f96cc08f34b9ea8c5a73839e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77466133"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET DoğrulamaContext.MemberName özel DataAnnotations.ValidationAttribute kullanırken NULL değildir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ve önceki sürümlerinde, <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> bir `null`özel <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>kullanırken, özellik döndürür. Ekim 2019 güncelleştirmesi öncesinde .NET Framework 4.8 sürümünde üye adını döndürür. [.NET Framework Ekim 2019 .NET](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) Framework 4.8 için Kalite `null` Toplama Önizlemesi ile başlayarak, varsayılan olarak döndürür, ancak bunun yerine üye adını döndürmeyi tercih edebilirsiniz. |
|Öneri|[.NET Framework Ekim 2019 .NET Framework](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) 4.8 ve sonraki sürümler için Kalite Toplama Önizlemesinde üye adını döndürmek için *web.config* dosyanıza aşağıdaki ayarı ekleyin:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Ekim 2019 güncelleştirmesi öncesinde .NET Framework 4.8 sürümünde, *bunu web.config* dosyanıza `null`eklemek önceki davranışı geri yükler ve özellik döndürür.|
|Kapsam|Bilinmiyor|
|Sürüm|4.8|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
