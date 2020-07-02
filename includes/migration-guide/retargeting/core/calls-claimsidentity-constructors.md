---
ms.openlocfilehash: b88f7d4a17f885b687d99ab9410a56039e176080
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614642"
---
### <a name="calls-to-claimsidentity-constructors"></a>ClaimsIdentity oluşturucuları çağrıları

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 ' den başlayarak, <xref:System.Security.Claims.ClaimsIdentity> bir parametreye sahip oluşturucuların özelliği ayarlama biçiminde bir değişiklik vardır <xref:System.Security.Principal.IIdentity?displayProperty=fullName> <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> . <xref:System.Security.Principal.IIdentity?displayProperty=fullName>Bağımsız değişken bir nesne ise <xref:System.Security.Claims.ClaimsIdentity> ve <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> Bu <xref:System.Security.Claims.ClaimsIdentity> nesnenin özelliği değilse `null` , <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> özelliği yöntemi kullanılarak iliştirilir <xref:System.Security.Claims.ClaimsIdentity.Clone> . Framework 4.6.1 ve önceki sürümlerde, <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> özelliği var olan bir başvuru olarak eklenir. Bu değişiklik nedeniyle .NET Framework 4.6.2 ile başlayarak, <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> Yeni <xref:System.Security.Claims.ClaimsIdentity> nesnenin özelliği <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> oluşturucunun bağımsız değişkeninin özelliğine eşit değildir <xref:System.Security.Principal.IIdentity?displayProperty=fullName> . .NET Framework 4.6.1 ve önceki sürümlerde, eşittir.

#### <a name="suggestion"></a>Öneri

Bu davranış istenerek, `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` uygulama yapılandırma dosyanızdaki anahtarı olarak ayarlayarak önceki davranışı geri yükleyebilirsiniz `true` . Bunun için aşağıdakileri `<runtime>` web.config dosyanızın bölümüne eklemeniz gerekir:

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />
  </runtime>
</configuration>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)>
