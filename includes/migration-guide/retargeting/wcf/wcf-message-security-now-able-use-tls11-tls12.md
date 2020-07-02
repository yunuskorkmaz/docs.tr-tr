---
ms.openlocfilehash: c646372104457e8bc5d418744847f3ee771c8d8b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614801"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>WCF ileti güvenliği artık TLS 1.1 ve TLS 1.2 kullanabiliyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,7 ' den başlayarak, müşteriler, uygulama yapılandırma ayarları aracılığıyla SSL 3.0 ve TLS 1.0 ' a ek olarak WCF ileti güvenliği 'nde TLS 1.1 veya TLS 1.2 'yi yapılandırabilir.

#### <a name="suggestion"></a>Öneri

.NET Framework 4,7 ' de, WCF ileti güvenliği 'nde TLS 1.1 ve TLS 1.2 desteği varsayılan olarak devre dışıdır. `<runtime>`app.config veya web.config dosyasının bölümüne aşağıdaki satırı ekleyerek etkinleştirebilirsiniz:

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4,7         |
| Tür    | Yeniden Hedefleme |
