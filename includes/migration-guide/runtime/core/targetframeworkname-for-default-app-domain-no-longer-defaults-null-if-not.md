---
ms.openlocfilehash: 4e685722271a8079e727ea9c2e0e501f68b30fc9
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497889"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>Varsayılan uygulama etki alanı için TargetFrameworkName, ayarlanmamışsa artık varsayılan olarak null değerini alır

#### <a name="details"></a>Ayrıntılar

<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>Açık olarak ayarlanmadığı takdirde, varsayılan uygulama etki alanında daha önce null idi. 4,6 ' den başlayarak, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> Varsayılan uygulama etki alanı için özelliği TargetFrameworkAttribute öğesinden türetilen varsayılan değere sahip olacaktır (varsa). Varsayılan olmayan uygulama etki alanları, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> açıkça geçersiz kılınmadıkça varsayılan uygulama etki alanından (varsayılan olarak 4,6 ' de null değeri yoktur) devralma yapmaya devam edecektir.

#### <a name="suggestion"></a>Öneri

Kodun, <xref:System.AppDomainSetup.TargetFrameworkName> varsayılan değer olarak null değerine bağlı olmaması için güncelleştirilmeleri gerekir. Bu özelliğin NULL olarak değerlendirilmeye devam etmesi gerekiyorsa, açıkça bu değere ayarlanabilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.AppDomainSetup.TargetFrameworkName`

-->
