---
ms.openlocfilehash: f007a2b81820a1d25a2d101b35f3a49e7794fec1
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859134"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>İş akışı sağlama için SHA1 MD5 ' değiştirildi

|   |   |
|---|---|
|Ayrıntılar|Visual Studio ile hata ayıklamayı desteklemek için iş akışı çalışma zamanı sağlama toplamı için bir karma algoritmasını kullanarak bir iş akışı örneği oluşturur. .NET Framework 4.6.2 ve önceki sürümleri, iş akışı sağlama toplamı karma FIPS etkin sistemlerinde sorunları nedeniyle MD5 algoritma kullanılır. .NET Framework 4.7 ile başlayarak, algoritma SHA1 değeridir. Kodunuzu bu sağlama toplamları kalıcı, uyumlu olacaktır.|
|Öneri|Kodunuz iş akışı örnekleri sağlama toplamı hata nedeniyle yüklenemiyor: ayar deneyin <code>AppContext</code> geçiş &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; true. Kod:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>Veya yapılandırma:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|`Scope`|Küçük|
|Version|4.7|
|Type|Yeniden Hedefleme|

