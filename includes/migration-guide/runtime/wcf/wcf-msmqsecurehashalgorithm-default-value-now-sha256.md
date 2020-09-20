---
ms.openlocfilehash: 7c0227980aa5d90f3788783088bcd7cd9509ed66
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770963"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>WCF MsmqSecureHashAlgorithm varsayılan değeri artık SHA256

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.1 başlayarak, MSMQ iletileri için WCF 'de varsayılan ileti imzalama algoritması SHA256 ' dir. .NET Framework 4,7 ve önceki sürümlerde, varsayılan ileti imzalama algoritması SHA1 ' dır.

#### <a name="suggestion"></a>Öneri

Bu değişiklik ile .NET Framework 4.7.1 veya sonraki bir sürümde uyumluluk sorunları yaşıyorsanız, app.config dosyanızın bölümüne aşağıdaki satırı ekleyerek değişikliği devre dışı bırakabilirsiniz `<runtime>` :

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; />
  </runtime>
</configuration>
```

| Name    | Değer   |
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
