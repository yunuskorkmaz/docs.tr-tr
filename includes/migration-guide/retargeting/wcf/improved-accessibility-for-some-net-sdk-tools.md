---
ms.openlocfilehash: 0b087fca59d60a086a9ea8b2bb19c09f646c3dfd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858938"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Bazı .NET SDK araçları için geliştirilmiş erişilebilirlik

|   |   |
|---|---|
|Ayrıntılar|.NET Framework SDK 4.7.1'de, SvcConfigEditor.exe ve SvcTraceViewer.exe araçları çeşitli erişilebilirlik sorunları nın giderilmesiyle geliştirilmiştir. Bunların çoğu tanımlanmayan bir ad veya belirli Kullanıcı Arabirimi otomasyon desenleri gibi küçük sorunlardır doğru uygulanmıyor. Birçok kullanıcı bu yanlış değerlerin farkında olmasa da, ekran okuyucular gibi yardımcı teknolojileri kullanan müşteriler bu SDK araçlarını daha erişilebilir bulur. Kesinlikle, bu düzeltmeler klavye odak sırası gibi bazı önceki davranışları değiştirir. Bu araçlardaki tüm erişilebilirlik düzeltmelerini almak için app.config dosyanıza aşağıdakileri yapabilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Edge|
|Sürüm|4.7.1|
|Tür|Yeniden Hedefleme|
