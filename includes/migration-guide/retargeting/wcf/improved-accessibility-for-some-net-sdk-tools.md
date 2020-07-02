---
ms.openlocfilehash: f78d15338aa49de5b729aca12964924a0df00ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614829"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Bazı .NET SDK araçları için iyileştirilmiş erişilebilirlik

#### <a name="details"></a>Ayrıntılar

.NET Framework SDK 4.7.1, SvcConfigEditor.exe ve SvcTraceViewer.exe araçları, değişen erişilebilirlik sorunlarını düzelterek geliştirilmiştir. Bunların çoğu, bir ad tanımlanmamış veya belirli UI Otomasyon desenlerinin doğru uygulanmadığını küçük sorunlardır. Birçok kullanıcı bu hatalı değerleri farkında olmasa da ekran okuyucular gibi yardımcı teknolojiler kullanan müşteriler bu SDK araçlarını daha erişilebilir bulacaktır. Kesinlikle, bu düzeltmeler klavye odağı sırası gibi önceki bazı davranışları değiştirir. Bu araçlarınızdaki tüm erişilebilirlik düzeltmelerini almak için app.config dosyanıza aşağıdaki adımları uygulayabilirsiniz:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false"/>
</runtime>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.7.1       |
| Tür    | Yeniden Hedefleme |
