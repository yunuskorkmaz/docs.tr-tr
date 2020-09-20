---
ms.openlocfilehash: 3cf1740565343558a85fdfa68957773468c28231
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770957"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>WCF PipeConnection. GetHashAlgorithm artık SHA256 kullanıyor

#### <a name="details"></a>Ayrıntılar

Windows Communication Foundation .NET Framework başlayarak, adlandırılmış kanallar için rastgele adlar oluşturmak üzere bir SHA256 karması kullanır. .NET Framework 4,7 ve önceki sürümlerde, bir SHA1 karması kullandı.

#### <a name="suggestion"></a>Öneri

Bu değişiklik ile .NET Framework 4.7.1 veya sonraki bir sürümde uyumluluk sorunuyla karşılaşırsanız, app.config dosyanızın bölümüne aşağıdaki satırı ekleyerek geri alabilirsiniz `<runtime>` :

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true" />
  </runtime>
</configuration>

| Name    | Value   |
|:--------|:--------|
| Scope   | Minor   |
| Version | 4.7.1   |
| Type    | Runtime |

#### Affected APIs

Not detectable via API analysis.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
