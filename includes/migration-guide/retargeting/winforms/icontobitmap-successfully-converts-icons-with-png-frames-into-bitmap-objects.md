---
ms.openlocfilehash: f4a5911787fa5f72be1dcd15c67b3f132c3f1110
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804545"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Icon.ToBitmap, PNG çerçeveli simgeleri Bitmap nesnelerine başarıyla dönüştürür

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6'yı hedefleyen uygulamalardan <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> başlayarak, yöntem PNG çerçeveli simgeleri Başarıyla Bitmap nesnelerine dönüştürür.<p/>.NET Framework 4.5.2 ve önceki sürümleri hedefleyen <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> uygulamalarda, <xref:System.ArgumentOutOfRangeException> Simge nesnesinin PNG çerçeveleri varsa yöntem bir özel durum oluşturur.<p/>Bu değişiklik, .NET Framework 4.6'yı hedeflemek için yeniden derlenen <xref:System.ArgumentOutOfRangeException> ve bir Simge nesnesi PNG çerçevesi olduğunda atılanlar için özel işleme uygulayan uygulamaları etkiler. .NET Framework 4.6 altında çalışırken, dönüştürme başarılı <xref:System.ArgumentOutOfRangeException> olur, artık bir atılmıştır ve bu nedenle özel durum işleyicisi artık çağrılmaz.|
|Öneri|Bu davranış istenmiyorsa, app.config dosyanızın <code>&lt;runtime&gt;</code> bölümüne aşağıdaki öğeyi ekleyerek önceki davranışı koruyabilirsiniz:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>app.config dosyası zaten öğeyi içeriyorsa, <code>AppContextSwitchOverrides</code> yeni değer aşağıdaki gibi değer özniteliği ile birleştirilmelidir:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|
