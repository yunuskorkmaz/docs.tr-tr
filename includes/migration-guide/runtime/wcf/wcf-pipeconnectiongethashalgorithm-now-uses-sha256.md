---
ms.openlocfilehash: 71f61f23a8b17459610d253766a99e594f09428e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857240"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>WCF PipeConnection.GetHashAlgorithm SHA256 artık kullanır.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ile başlayarak, Windows Communication Foundation SHA256 karma rastgele adları için adlandırılmış kanallar oluşturmak için kullanır. .NET Framework 4.7 ve önceki sürümlerinde SHA1 karması kullanılır.|
|Öneri|.NET Framework 4.7.1 Bu değişiklik ile uyumluluk sorunu içine çalıştırın ya da daha sonra bunu aşağıdaki satırı ekleyerek çevirme <code>&lt;runtime&gt;</code> app.config dosyanıza bölümünü:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|`Scope`|Küçük|
|Version|4.7.1|
|Type|Çalışma zamanı|

