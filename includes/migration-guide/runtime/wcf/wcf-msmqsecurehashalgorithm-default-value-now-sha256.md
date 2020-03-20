---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857253"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>WCF MsmqSecureHashAlgorithm varsayılan değeri şimdi SHA256 olduğunu

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ile başlayarak, Msmq iletileri için WCF'deki varsayılan ileti imzalama algoritması SHA256'dır. .NET Framework 4.7 ve önceki sürümlerinde varsayılan ileti imzalama algoritması SHA1'dir.|
|Öneri|.NET Framework 4.7.1 veya sonraki düzey bu değişiklikle uyumluluk sorunlarıyla karşınıza çıkarsa, app.config <code>&lt;runtime&gt;</code>dosyanızın bölümüne aşağıdaki satırı ekleyerek değişikliği devre dışı kullanabilirsiniz:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.1|
|Tür|Çalışma Zamanı|
