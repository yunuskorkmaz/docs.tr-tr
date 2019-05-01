---
ms.openlocfilehash: 6dd7f2a2f6dec306940650beee58104b20788bdb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758420"
---
### <a name="calls-to-claimsidentity-constructors"></a>Claimsıdentity oluşturucular çağrıları

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ile başlayarak, nasıl bir değişiklik olduğunda <xref:System.Security.Claims.ClaimsIdentity> oluşturucularla bir <xref:System.Security.Principal.IIdentity?displayProperty=name> parametre kümesi <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> özelliği. Varsa <xref:System.Security.Principal.IIdentity?displayProperty=name> bağımsız değişkeni bir <xref:System.Security.Claims.ClaimsIdentity> nesnesi ve <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> , söz konusu özellik <xref:System.Security.Claims.ClaimsIdentity> nesne değil <code>null</code>, <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> özelliği kullanılarak bağlı <xref:System.Security.Claims.ClaimsIdentity.Clone> yöntemi. Framework 4.6.1 ve önceki sürümlerinde, <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> var olan bir başvuru olarak ekli özellik. .NET Framework 4.6.2, ile başlayarak, bu değişiklik nedeniyle <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> yeni özellik <xref:System.Security.Claims.ClaimsIdentity> nesnesi eşit değil <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> oluşturucunun özelliği <xref:System.Security.Principal.IIdentity?displayProperty=name> bağımsız değişken. .NET Framework 4.6.1 ve önceki sürümlerinde eşittir.|
|Öneri|Bu davranış, istenmeyen ise ayarlayarak önceki davranış geri yükleyebilirsiniz <code>Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity</code> geçiş yapmak için uygulama yapılandırma dosyasında <code>true</code>. Bu, aşağıdaki eklemenizi gerektirir <code>&lt;runtime&gt;</code> bölümü web.config dosyanızın:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)?displayProperty=nameWithType></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})?displayProperty=nameWithType></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)?displayProperty=nameWithType></li></ul>|
