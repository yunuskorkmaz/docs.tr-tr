---
ms.openlocfilehash: c5a061dffa1deb66e1769d6ec70dfa2155ac6a31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615769"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>CreateDefaultAuthorizationContext 'in null bir bağımsız değişkenle çağrılması değiştirildi

#### <a name="details"></a>Ayrıntılar

<xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName>Null authorizationPolicies bağımsız değişkeni ile öğesine yapılan bir çağrı tarafından döndürülen uygulanması, <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> .NET Framework 4,6 ' deki uygulamasını değiştirdi.

#### <a name="suggestion"></a>Öneri

Nadir durumlarda, özel kimlik doğrulaması kullanan WCF uygulamaları davranış farklarını görebilirler. Bu gibi durumlarda, önceki davranış iki şekilde geri yüklenebilir:

- Uygulamanızı 4,6 ' den daha önceki bir .NET Framework sürümünü hedeflemek için yeniden derleyin. IIS tarafından barındırılan hizmetler için, `<httpRuntime targetFramework="x.x">` .NET Framework önceki bir sürümünü hedeflemek için öğesini kullanın.
- app.config dosyanızın bölümüne aşağıdaki satırı ekleyin `<appSettings>` :

    ```xml
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />
    ```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.6         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType>
