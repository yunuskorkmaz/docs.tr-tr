---
ms.openlocfilehash: 19e0524f4d40517f3e305b2397e628e0478da8f9
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803560"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a>İş akışı XOML dosya sağlama toplamı için SHA256 MD5 değiştirildi

|   |   |
|---|---|
|Ayrıntılar|İş akışı XOML dosyaları derleme içeren projeler, iş akışı XOML tabanlı Visual Studio ile hata ayıklamayı desteklemek için XOML dosyası içeriğinin bir sağlama toplamı olarak oluşturulan kodu yer aldığı bir <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> değeri. .NET Framework 4.7.2 ve önceki sürümleri, bu sağlama toplamı karma FIPS etkin sistemlerinde sorunları nedeniyle MD5 algoritma kullanılır. .NET Framework 4.8 ile başlayarak, kullanılan algoritması SHA256 olan. WorkflowMarkupSourceAttribute.MD5Digest ile uyumlu olması için yalnızca ilk 16 baytlık oluşturulan sağlama toplamı kullanılır. Bu hata ayıklama sırasında sorunlara neden olabilir. Projenizi yeniden oluşturmanız gerekebilir.|
|Öneri|Projenizi yeniden oluşturma sorunu çözmezse, ayarı deneyin <code>AppContext</code> geçiş &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; true. Kod:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>Veya bir yapılandırma dosyasında (Bu için kullanmakta olduğunuz MSBuild.exe MSBuild.exe.config olması gerekir):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.8|
|Tür|Yeniden Hedefleme|

