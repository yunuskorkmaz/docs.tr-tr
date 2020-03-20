---
ms.openlocfilehash: f59c9f048bb3cd3f425e36b931302258fcf693f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803560"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a>İş akışı XOML dosya kontrol leri MD5'ten SHA256'ya değiştirildi

|   |   |
|---|---|
|Ayrıntılar|Visual Studio ile XOML tabanlı iş aktarımlarını desteklemek için, XOML dosyaları içeren iş akışı projeleri oluşturulduğunda, XOML dosyasının içeriğinin bir denetim umması <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> değer olarak oluşturulan koda dahil edilir. .NET Framework 4.7.2 ve önceki sürümlerinde, bu denetim karma fips etkin sistemlerde sorunlara neden MD5 algoritması kullanılır. .NET Framework 4.8 ile başlayarak kullanılan algoritma SHA256'dır. WorkflowMarkupSourceAttribute.MD5Digest ile uyumlu olmak için, oluşturulan checksum sadece ilk 16 bayt kullanılır. Bu hata ayıklama sırasında sorunlara neden olabilir. Projenizi yeniden oluşturmanız gerekebilir.|
|Öneri|Projenizi yeniden oluşturma sorunu çözmüyorsa <code>AppContext</code> Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum'u&quot; doğru ayarlamayı &quot;deneyin. Kod olarak:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>Veya bir yapılandırma dosyasında (bu kullandığınız MSBuild.exe için MSBuild.exe.config olması gerekir):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.8|
|Tür|Yeniden Hedefleme|
