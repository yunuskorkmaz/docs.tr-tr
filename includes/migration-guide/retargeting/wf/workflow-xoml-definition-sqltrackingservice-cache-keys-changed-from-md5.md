---
ms.openlocfilehash: 4254cceab0048341b32fe5babf53b5ea3e5a52d6
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "72846993"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>İş akışı XOML tanımı ve SqlTrackingService önbellek anahtarları MD5 'den SHA256 'e değişti

|   |   |
|---|---|
|Ayrıntılar|' Deki Iş akışı çalışma zamanı, XOML içinde tanımlanan iş akışı tanımlarının bir önbelleğini tutar. SqlTrackingService, dizeler tarafından girilen bir önbelleği de tutar. Bu önbellekler, sağlama toplamı karma değeri içeren değerlere göre anahtarlanır. .NET Framework 4.7.2 ve önceki sürümlerde, bu sağlama toplamı karma, FIPS özellikli sistemlerde sorunlara neden olan MD5 algoritmasını kullandı. 4,8 .NET Framework başlayarak kullanılan algoritma SHA256. Bu değişiklik ile bir uyumluluk sorunu olmaması gerekir, çünkü Iş akışı çalışma zamanı ve SqlTrackingService her başlatıldığında değerler yeniden hesaplanır. Bununla birlikte, müşterilerin, gerekirse eski karma algoritmanın kullanımına geri dönüşmesini sağlayan bir olağandışı şekilde sunuyoruz.|
|Öneri|Bu değişiklik iş akışlarını yürütürken bir sorun yaparsa <code>AppContext</code> anahtarlarından birini veya her ikisini ayarlamayı deneyin:<ul><li>Switch. System. Workflow. Runtime. UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; true olarak &quot;.</li><li>Switch. System. Workflow. Runtime. UseLegacyHashForSqlTrackingCacheKey&quot; true olarak &quot;.</li></ul>Kod:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>Yapılandırma dosyasında (bunun <xref:System.Workflow.Runtime.WorkflowRuntime> nesnesi oluşturan uygulamanın yapılandırma dosyasında olması gerekir):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Version|4,8|
|Tür|Yeniden Hedefleme|
