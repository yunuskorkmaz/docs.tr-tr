---
ms.openlocfilehash: 3b7b50700541649a785fa9bbe3ecc56c2697fbfc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859211"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>WCF ileti güvenliğini TLS1.1 ve TLS1.2 kullanabilir

|   |   |
|---|---|
|Ayrıntılar|İçinde .NET Framework 4.7 başlayarak, müşterilerin TLS1.1 ya da TLS1.2 SSL3.0 ve TLS1.0 yanı sıra WCF ileti güvenliğini uygulama yapılandırma ayarları ile yapılandırabilirsiniz.|
|Öneri|.NET Framework 4.7 WCF ileti güvenliğini TLS1.1 ve TLS1.2 için destek, varsayılan olarak devre dışıdır. Aşağıdaki satırı ekleyerek etkinleştirebilirsiniz <code>&lt;runtime&gt;</code> app.config veya web.config dosyasının:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|`Scope`|Kenar|
|Version|4.7|
|Type|Yeniden Hedefleme|

