---
ms.openlocfilehash: 4bc8db52efdfe483acb4f6b6e33c4fa7716e0b79
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770856"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>svcTraceViewer ComboBox yüksek karşıtlık değişikliği

#### <a name="details"></a>Ayrıntılar

[Microsoft hizmet Izleme Görüntüleyicisi aracında](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox denetimleri bazı yüksek karşıtlıklı temalarda doğru renkte görüntülenmedi. Sorun .NET Framework 4.7.2 içinde düzeltildi. Ancak, .NET Framework SDK geri uyumluluk gereksinimleri nedeniyle, bu düzeltmeler müşterilere varsayılan olarak görünmez. .NET 4,8, svcTraceViewer.exe.config dosyasına aşağıdaki [AppContext yapılandırma anahtarlarını](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ekleyerek bu değişikliği yüzeylerine ekler:

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

#### <a name="suggestion"></a>Öneri

Yüksek karşıtlık davranış değişikliğini istemiyorsanız, svcTraceViewer.exe.config dosyasından aşağıdaki bölümü kaldırarak devre dışı bırakabilirsiniz:

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

| Name    | Değer   |
|:--------|:--------|
| Kapsam   | Edge    |
| Sürüm | 4,8     |
| Tür    | Çalışma Zamanı |

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
