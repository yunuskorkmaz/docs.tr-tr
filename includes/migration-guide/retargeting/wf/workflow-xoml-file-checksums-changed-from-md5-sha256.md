---
ms.openlocfilehash: b1910bf0338bccd77ad9e983990d4d193698ec1f
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96477455"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a>İş akışı XOML dosya sağlama toplamı, MD5 'den SHA256 'e değişti

#### <a name="details"></a>Ayrıntılar

Visual Studio ile XOML tabanlı iş akışlarının hatalarını ayıklamayı desteklemek için, XOML dosyalarını içeren iş akışı projeleri derleme oluştururken, XOML dosyası içeriğinin bir sağlama toplamı bir değer olarak oluşturulan koda dahil edilir <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> . .NET Framework 4.7.2 ve önceki sürümlerde, bu sağlama toplamı karma, FIPS özellikli sistemlerde sorunlara neden olan MD5 algoritmasını kullandı. 4,8 .NET Framework başlayarak kullanılan algoritma SHA256. WorkflowMarkupSourceAttribute. MD5Digest ile uyumlu olmak için, oluşturulan sağlama toplamı yalnızca ilk 16 bayt kullanılır. Bu, hata ayıklama sırasında sorunlara neden olabilir. Projenizi yeniden derlemeniz gerekebilir.

#### <a name="suggestion"></a>Öneri

Projenizin yeniden oluşturulması sorunu çözmezse, `AppContext` &quot;Switch.SysDıtem. Workflow. ComponentModel. UseLegacyHashForXomlFileChecksum anahtarını &quot; true olarak ayarlamayı deneyin. Kodda:

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>

Ya da bir yapılandırma dosyasında (Bu, kullanmakta olduğunuz MSBuild.exe için MSBuild.exe.config olması gerekir):

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Ad    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.8         |
| Tür    | Yeniden Hedefleme |
