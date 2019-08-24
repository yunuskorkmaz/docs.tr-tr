---
ms.openlocfilehash: 3b94c88809513e31a5f226bcfce39abbfa4de378
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017378"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>Özel Dataaçıklamalarda. ValidationAttribute kullanılırken ASP.NET ValidationContext. MemberName NULL değil

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ve önceki sürümlerde, özel <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> bir kullanırken özelliği döndürür <code>null</code>.  .NET Framework 4,8 ' de, üye adını döndürür.|
|Öneri|Önceki davranışı geri yüklemek için, uygulama yapılandırma dosyanıza aşağıdaki ayarı ekleyin:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Yeni davranışı açıkça kabul etmeniz gerektiğinde, bu davranış yaklaşan bir hizmet sürümünde değişecektir. `aspnet:GetValidationMemberName` Anahtar `ValidationAttribute` olarak`true`ayarlandıysa, özelliği bir özel için null olmayan bir değer döndürür.|
|Kapsam|Bilinmiyor|
|Sürüm|4.8|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
