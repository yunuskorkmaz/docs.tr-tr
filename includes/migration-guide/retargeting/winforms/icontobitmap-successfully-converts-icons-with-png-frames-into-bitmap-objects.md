---
ms.openlocfilehash: f4a5911787fa5f72be1dcd15c67b3f132c3f1110
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805249"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Icon.ToBitmap, PNG çerçevelerle simgeler başarıyla bit eşlem nesnelerine dönüştürür.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4. 6'ü hedefleyen uygulamaları ile başlayan <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yöntemi başarıyla PNG çerçevelerle simgeler bit eşlem nesnelerine dönüştürür.<p/>.NET Framework 4.5.2 ve önceki sürümleri hedefleyen uygulamalarda <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yöntem bir <xref:System.ArgumentOutOfRangeException> PNG kare simge nesnesi varsa, özel durum.<p/>Bu değişiklik, .NET Framework 4.6 hedefleyecek şekilde derlenir ve özel işlem uygulamak uygulamaları etkiler. <xref:System.ArgumentOutOfRangeException> PNG kare bir simge nesnesi sahip olduğunda oluşturulur. .NET Framework 4. 6'altında çalışırken, dönüştürme başarılı bir <xref:System.ArgumentOutOfRangeException> Hayır artık oluşturulur ve bu nedenle özel durum işleyicisi artık çağrılır.|
|Öneri|Bu davranış, istenmeyen ise, önceki davranışı şu öğeye ekleyerek koruyabilirsiniz <code>&lt;runtime&gt;</code> app.config dosyanıza bölümünü:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>App.config dosyasını zaten varsa <code>AppContextSwitchOverrides</code> öğesi, bu gibi değer özniteliğine sahip yeni bir değer birleştirilmiş:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|
