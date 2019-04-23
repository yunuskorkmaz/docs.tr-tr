---
ms.openlocfilehash: f59c9f048bb3cd3f425e36b931302258fcf693f5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982252"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a>İş akışı XOML dosya sağlama toplamı için SHA256 MD5 değiştirildi

|   |   |
|---|---|
|Ayrıntılar|İş akışı XOML dosyaları derleme içeren projeler, iş akışı XOML tabanlı Visual Studio ile hata ayıklamayı desteklemek için XOML dosyası içeriğinin bir sağlama toplamı olarak oluşturulan kodu yer aldığı bir <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> değeri. .NET Framework 4.7.2 ve önceki sürümleri, bu sağlama toplamı karma FIPS etkin sistemlerinde sorunları nedeniyle MD5 algoritma kullanılır. .NET Framework 4.8 ile başlayarak, kullanılan algoritması SHA256 olan. WorkflowMarkupSourceAttribute.MD5Digest ile uyumlu olması için yalnızca ilk 16 baytlık oluşturulan sağlama toplamı kullanılır. Bu hata ayıklama sırasında sorunlara neden olabilir. Projenizi yeniden oluşturmanız gerekebilir.|
|Öneri|Projenizi yeniden oluşturma sorunu çözmezse, ayarı deneyin <code>AppContext</code> geçiş &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; true. Kod:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>Veya bir yapılandırma dosyasında (Bu için kullanmakta olduğunuz MSBuild.exe MSBuild.exe.config olması gerekir):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.8|
|Tür|Yeniden Hedefleme|
