---
ms.openlocfilehash: 9ec5fa379556dedeaa7a35e34f004340ab47a39c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804516"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>CreateDefaultAuthorizationContext'ı null bağımsız değişkenle arama

|   |   |
|---|---|
|Ayrıntılar|İade edilen <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=name> inanın null <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=name> authorizationPolicies argümanı ile birlikte uygulanması .NET Framework 4.6'daki uygulamasını değiştirmiştir.|
|Öneri|Nadir durumlarda, özel kimlik doğrulaması kullanan WCF uygulamaları davranış farklılıkları görebilir. Bu gibi durumlarda, önceki davranış iki şekilde de geri yüklenebilir:<ol><li>.NET Framework'ün 4,6'dan daha önceki bir sürümünü hedeflemek için uygulamanızı yeniden derle. IIS tarafından barındırılan &lt;hizmetler için,.NET&quot;Framework'ün önceki bir sürümünü hedeflemek için httpRuntime targetFramework= x.x&quot;  / &gt; öğesini kullanın.</li><li>App.config dosyanızın bölümüne <code>&lt;appSettings&gt;</code> aşağıdaki satırı ekleyin:<code>&lt;add key=&quot;appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext&quot; value=&quot;true&quot; /&gt;</code></li></ol>|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType></li></ul>|
