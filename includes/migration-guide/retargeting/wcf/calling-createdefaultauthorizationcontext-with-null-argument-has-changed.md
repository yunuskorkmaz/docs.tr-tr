---
ms.openlocfilehash: 9ec5fa379556dedeaa7a35e34f004340ab47a39c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59234514"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>Null bir bağımsız değişkenle CreateDefaultAuthorizationContext arama değişti

|   |   |
|---|---|
|Ayrıntılar|Uygulamasını <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=name> bir çağrı tarafından döndürülen <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=name> ile bir null authorizationPolicies bağımsız değişkeni, uygulama .NET Framework 4.6 değişti.|
|Öneri|Nadiren de olsa, davranışsal farklılıklar özel kimlik doğrulama kullanan WCF uygulamaları görebilirsiniz. Bu gibi durumlarda, önceki davranışı iki yoldan biriyle geri yüklenebilir:<ol><li>Uygulamanızı .NET Framework'ün 4.6 daha önceki sürümünü hedefleyecek şekilde yeniden derleyin. IIS tarafından barındırılan hizmetleri için &lt;httpRuntime targetFramework =&quot;x.x&quot;  / &gt; .NET Framework'ün önceki sürümünü hedefleyecek şekilde öğesi.</li><li>Aşağıdaki satırı ekleyin <code>&lt;appSettings&gt;</code> app.config dosyanıza bölümünü: <code>&lt;add key=&quot;appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext&quot; value=&quot;true&quot; /&gt;</code></li></ol>|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType></li></ul>|
