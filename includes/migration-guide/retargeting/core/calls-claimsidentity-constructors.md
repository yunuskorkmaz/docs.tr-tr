---
ms.openlocfilehash: c10d617e07ca2fa0239298d449d93cf833b83fce
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275043"
---
### <a name="calls-to-claimsidentity-constructors"></a>İddialara ÇağrıLarKimlik yapıcıları

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ile başlayarak, parametreli <xref:System.Security.Claims.ClaimsIdentity> yapıcıların <xref:System.Security.Principal.IIdentity?displayProperty=name> <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> özelliği nasıl ayarlayıştAma şeklinde bir değişiklik vardır. <xref:System.Security.Principal.IIdentity?displayProperty=name> Bağımsız değişken bir <xref:System.Security.Claims.ClaimsIdentity> nesneise <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> ve bu <xref:System.Security.Claims.ClaimsIdentity> nesnenin <code>null</code>özelliği <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> değilse, özellik <xref:System.Security.Claims.ClaimsIdentity.Clone> yöntem kullanılarak eklenir. Çerçeve 4.6.1 ve önceki sürümlerde, <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> özellik varolan bir başvuru olarak eklenir. Bu değişiklik ten dolayı, .NET Framework 4.6.2 ile <xref:System.Security.Claims.ClaimsIdentity> başlayarak, yeni <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> nesnenin <xref:System.Security.Principal.IIdentity?displayProperty=name> <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> özelliği oluşturucubağımsız değişkeninin özelliğine eşit değildir. .NET Framework 4.6.1 ve önceki sürümlerinde eşittir.|
|Öneri|Bu davranış istenmiyorsa, uygulama yapılandırma dosyanızdaki <code>Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity</code> anahtarı <code>true</code>'ya ayarlayarak önceki davranışı geri yükleyebilirsiniz. Bu, web.config dosyanızın <code>&lt;runtime&gt;</code> bölümüne aşağıdakileri eklemenizi gerektirir:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Edge|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)></li></ul>|
