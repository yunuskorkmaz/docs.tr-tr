---
ms.openlocfilehash: 811b1a91169eeebfa056d9ecdb07d342d3b32d85
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615770"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Icon. ToBitmap, PNG çerçevelerinden simgeleri bit eşlem nesnelerine başarıyla dönüştürür

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,6 ' i hedefleyen uygulamalarla başlayarak, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> YÖNTEMI png çerçevelerinden simgeleri bit eşlem nesnelerine başarıyla dönüştürür.<p/>.NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> <xref:System.ArgumentOutOfRangeException> SIMGE nesnesi png çerçevelerdeyse Yöntem bir özel durum oluşturur.<p/>Bu değişiklik, .NET Framework 4,6 ' i hedefleyecek ve <xref:System.ArgumentOutOfRangeException> bir simge NESNESI png çerçevesine sahip olduğunda oluşturulan için özel işleme uygulayan uygulamaları etkiler. .NET Framework 4,6 altında çalışırken, dönüştürme başarılı olur, <xref:System.ArgumentOutOfRangeException> artık oluşturulmaz ve bu nedenle özel durum işleyicisi artık çağrılmayacaktır.

#### <a name="suggestion"></a>Öneri

Bu davranış istenmez ise, app.config dosyanızın bölümüne aşağıdaki öğeyi ekleyerek önceki davranışı koruyabilirsiniz `<runtime>` :

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>

app.config dosyası öğesi zaten içeriyorsa `AppContextSwitchOverrides` , yeni değer şöyle bir değer özniteliğiyle birleştirilmelidir:

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.6         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType>
