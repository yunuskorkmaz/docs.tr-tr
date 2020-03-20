---
ms.openlocfilehash: 4254cceab0048341b32fe5babf53b5ea3e5a52d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72846993"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>İş akışı XOML tanımı ve SqlTrackingService önbellek anahtarları MD5'ten SHA256'ya değiştirildi

|   |   |
|---|---|
|Ayrıntılar|İş Akışı Runtime xoml tanımlanan iş akışı tanımları bir önbellek tutar. SqlTrackingService ayrıca dizeleri tarafından anahtarlı bir önbellek tutar. Bu önbellekler, checksum karma değerini içeren değerlertarafından anahtarlanır. .NET Framework 4.7.2 ve önceki sürümlerinde, bu denetim karma fips etkin sistemlerde sorunlara neden MD5 algoritması kullanılır. .NET Framework 4.8 ile başlayarak kullanılan algoritma SHA256'dır. Bu değişiklikle uyumluluk sorunu olmamalıdır, çünkü Değerler Her İş Akışı Çalışma Süresi ve SqlTrackingService başlatıldığında yeniden hesaplanır. Ancak, müşterilerin gerekirse eski karma algoritmasının kullanımına geri dönmelerine olanak tanıyan tuhaflıklar sağladık.|
|Öneri|Bu değişiklik iş akışlarını yürütürken bir sorun oluşturuyorsa, anahtarlardan birini veya her ikisini ayarlamayı <code>AppContext</code> deneyin:<ul><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; doğru.</li><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; doğru.</li></ul>Kod:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>Veya yapılandırma dosyasında (bu <xref:System.Workflow.Runtime.WorkflowRuntime> nesneyi oluşturan uygulama için config dosyasında olması gerekir):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.8|
|Tür|Yeniden Hedefleme|
