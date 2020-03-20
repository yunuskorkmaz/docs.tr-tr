---
ms.openlocfilehash: 318609c15d2e0b9a7ee59b38463735b33ef87974
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857240"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>WCF PipeConnection.GetHashAlgorithm şimdi SHA256 kullanır

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ile başlayarak, Windows Communication Foundation adlandırılmış borular için rasgele adlar oluşturmak için sha256 karma kullanır. .NET Framework 4.7 ve önceki sürümlerinde SHA1 karma kullanılmıştır.|
|Öneri|.NET Framework 4.7.1 veya sonraki düzey bu değişiklikle uyumluluk sorunuyla karşınıza çıkarsa, app.config dosyanızın <code>&lt;runtime&gt;</code> bölümüne aşağıdaki satırı ekleyerek bu değişikliği devre dışı kullanabilirsiniz:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.1|
|Tür|Çalışma Zamanı|
