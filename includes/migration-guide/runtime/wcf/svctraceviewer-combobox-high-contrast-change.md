---
ms.openlocfilehash: cc6d96bd614ff015ae2125c0f1477e18a91a68f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802642"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>svcTraceViewer ComboBox yüksek kontrast değişimi

|   |   |
|---|---|
|Ayrıntılar|Microsoft [Service Trace Viewer aracında,](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)ComboBox denetimleri belirli yüksek karşıtlık temalarında doğru renkte görüntülenmedi. Sorun .NET Framework 4.7.2'de giderilmiştir. Ancak, .NET Framework SDK geriye dönük uyumluluk gereksinimleri nedeniyle, düzeltme varsayılan olarak müşteriler tarafından görülemedi. .NET 4.8 svcTraceViewer.exe.config dosyasına aşağıdaki [AppContext yapılandırma anahtarları](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ekleyerek bu değişikliği yüzeyler:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Öneri|<ul><li>Yüksek karşıtlık davranış değişikliğine sahip olmak istemiyorsanız, svcTraceViewer.exe.config dosyasından aşağıdaki bölümü kaldırarak değişikliği nasıl devre dışı kullanabilirsiniz:</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Edge|
|Sürüm|4.8|
|Tür|Çalışma Zamanı|
