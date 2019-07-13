---
ms.openlocfilehash: a2d4b7592727ca20ee79867094d6972eb9c4baed
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857253"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>WCF MsmqSecureHashAlgorithm varsayılan değer SHA256 şimdi:

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ile başlayarak, imza algoritması wcf'de Msmq iletileri için varsayılan SHA256 iletisidir. .NET Framework 4.7 ve önceki sürümleri, imza algoritması varsayılan ileti SHA1 ' dir.|
|Öneri|.NET Framework 4.7.1 uyumluluk sorunları bu değişikliği halinde çalıştırın ya da daha sonra değişikliğin aşağıdaki satırı ekleyerek çevirme <code>&lt;runtime&gt;</code>app.config dosyanıza bölümünü:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|`Scope`|Küçük|
|Version|4.7.1|
|Type|Çalışma zamanı|

