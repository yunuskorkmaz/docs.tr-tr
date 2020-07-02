---
ms.openlocfilehash: 7a7ecf052276fe8e62463498b83230d466630c79
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616296"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>İş akışı XOML tanımı ve SqlTrackingService önbellek anahtarları MD5 'den SHA256 'e değişti

#### <a name="details"></a>Ayrıntılar

' Deki Iş akışı çalışma zamanı, XOML içinde tanımlanan iş akışı tanımlarının bir önbelleğini tutar. SqlTrackingService, dizeler tarafından girilen bir önbelleği de tutar. Bu önbellekler, sağlama toplamı karma değeri içeren değerlere göre anahtarlanır. .NET Framework 4.7.2 ve önceki sürümlerde, bu sağlama toplamı karma, FIPS özellikli sistemlerde sorunlara neden olan MD5 algoritmasını kullandı. 4,8 .NET Framework başlayarak kullanılan algoritma SHA256. Bu değişiklik ile bir uyumluluk sorunu olmaması gerekir, çünkü Iş akışı çalışma zamanı ve SqlTrackingService her başlatıldığında değerler yeniden hesaplanır. Bununla birlikte, müşterilerin, gerekirse eski karma algoritmanın kullanımına geri dönüşmesini sağlayan bir olağandışı şekilde sunuyoruz.

#### <a name="suggestion"></a>Öneri

Bu değişiklik iş akışlarını yürütürken bir sorun yaparsa, anahtarların birini veya her ikisini ayarlamayı deneyin `AppContext` :

- &quot;Switch.SysTem. Workflow. Runtime. UseLegacyHashForWorkflowDefinitionDispenserCacheKey &quot; true.
- &quot;Switch.SysTem. Workflow. Runtime. UseLegacyHashForSqlTrackingCacheKey &quot; true.
Kod:

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>

Ya da yapılandırma dosyasında (Bu nesneyi oluşturan uygulamanın yapılandırma dosyasında olması gerekir <xref:System.Workflow.Runtime.WorkflowRuntime> ):

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4,8         |
| Tür    | Yeniden Hedefleme |
