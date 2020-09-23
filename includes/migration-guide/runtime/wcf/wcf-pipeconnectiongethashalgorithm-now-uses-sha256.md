---
ms.openlocfilehash: 9f5f238e3d4222af1da3a1713e1b3e65de6e6f49
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91024982"
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
```

| Ad    | Değer   |
|:--------|:--------|
| Kapsam   | İkincil   |
| Sürüm | 4.7.1   |
| Tür    | Çalışma Zamanı |

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
