---
ms.openlocfilehash: 6a6c0af9cc0f3e5d1bbc3a4462a9ff7eaa748a5f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497849"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>svcTraceViewer ComboBox yüksek karşıtlık değişikliği

#### <a name="details"></a>Ayrıntılar

[Microsoft hizmet Izleme Görüntüleyicisi aracında](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox denetimleri bazı yüksek karşıtlıklı temalarda doğru renkte görüntülenmedi. Sorun .NET Framework 4.7.2 içinde düzeltildi. Ancak, .NET Framework SDK geri uyumluluk gereksinimleri nedeniyle, bu düzeltmeler müşterilere varsayılan olarak görünmez. .NET 4,8, svcTraceViewer.exe.config dosyasına aşağıdaki [AppContext yapılandırma anahtarlarını](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ekleyerek bu değişikliği yüzeylerine ekler:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

#### <a name="suggestion"></a>Öneri

<ul><li>Değişiklik, yüksek karşıtlık davranış değişikliğini yapmak istemiyorsanız, svcTraceViewer.exe.config dosyasından aşağıdaki bölümü kaldırarak devre dışı bırakabilirsiniz:</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,8|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
