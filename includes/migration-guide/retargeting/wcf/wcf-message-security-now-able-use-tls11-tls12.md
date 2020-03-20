---
ms.openlocfilehash: 0a3dc43ebdc58d54675f2264a8ee56d9f4358cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859211"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>WCF mesaj güvenliği artık TLS1.1 ve TLS1.2'yi kullanabiliyor

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7'den başlayarak, müşteriler uygulama yapılandırma ayarları üzerinden SSL3.0 ve TLS1.0'a ek olarak WCF mesaj güvenliğinde TLS1.1 veya TLS1.2'yi yapılandırabilirler.|
|Öneri|.NET Framework 4.7'de, WCF ileti güvenliğinde TLS1.1 ve TLS1.2 desteği varsayılan olarak devre dışı bırakılır. App.config veya web.config <code>&lt;runtime&gt;</code> dosyasıbölümüne aşağıdaki satırı ekleyerek etkinleştirebilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Edge|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
