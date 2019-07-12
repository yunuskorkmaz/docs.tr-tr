---
ms.openlocfilehash: 9c54572b8dcedaa103db8503cfc1155b4698c3ed
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803505"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a>İş akışı XAML sağlama toplamı için SHA256 SHA1 değiştirilmiş sembolleri

|   |   |
|---|---|
|Ayrıntılar|Visual Studio ile hata ayıklamayı desteklemek için iş akışı çalışma zamanı sağlama toplamı için bir karma algoritmasını kullanarak bir iş akışı XAML dosyası oluşturur. .NET Framework 4.6.2 ve önceki sürümleri, iş akışı sağlama toplamı karma FIPS etkin sistemlerinde sorunları nedeniyle MD5 algoritma kullanılır. .NET Framework 4.7 ile başlayarak, varsayılan algoritma SHA1 için değiştirildi. .NET Framework 4.8 ile başlayarak, varsayılan algoritması SHA256 için değiştirildi.|
|Öneri|İş akışı örnekleri yüklenemedi veya sağlama toplamı hata nedeniyle uygun simgeleri bulmak için kodunuzu silemiyor ayarı deneyin <code>AppContext</code> geçiş &quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot; true. Kod:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot;, true);&#13;&#10;</code></pre>Veya yapılandırma:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.8|
|Tür|Yeniden Hedefleme|

