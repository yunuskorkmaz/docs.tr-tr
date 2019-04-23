---
ms.openlocfilehash: cc6d96bd614ff015ae2125c0f1477e18a91a68f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982165"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>svcTraceViewer ComboBox yüksek karşıtlık Değiştir

|   |   |
|---|---|
|Ayrıntılar|İçinde [Microsoft hizmet izleme Görüntüleyicisi aracı](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox denetimleri içinde doğru belirli yüksek karşıtlıklı Tema rengi değil görüntülendi. .NET Framework 4.7.2 sorunu düzeltildi. Ancak, .NET Framework SDK geriye dönük uyumluluk gereksinimleri nedeniyle, düzeltme müşteriler varsayılan olarak görünür değil. .NET 4.8 aşağıdakileri ekleyerek bu değişikliği yüzeyler [AppContext yapılandırma anahtarları](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) svcTraceViewer.exe.config dosyaya:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Öneri|<ul><li>Yüksek Karşıtlık olmasını istemiyorsanız değişikliği geri çevirmek için davranışı değiştirmek nasıl, bunu aşağıdaki bölümde svcTraceViewer.exe.config dosyadan kaldırarak devre dışı bırakabilirsiniz:</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.8|
|Tür|Çalışma zamanı|
