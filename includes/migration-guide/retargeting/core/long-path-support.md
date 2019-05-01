---
ms.openlocfilehash: 506218195417548880a9d8d10508a570a7769682
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640114"
---
### <a name="long-path-support"></a>Uzun yol desteği

|   |   |
|---|---|
|Ayrıntılar|Uygulamalarla hedefleyen .NET Framework 4.6.2, uzun yollar (en fazla 32 K karakterler) desteklenir ve 260 karakter başlangıç (veya <code>MAX_PATH</code>) yol uzunluğu sınırlama kaldırıldı. .NET Framework 4.6.2 hedeflemek için yeniden derlenen uygulamalar için daha önce oluşturdu yolları kod bir <xref:System.IO.PathTooLongException?displayProperty=name> yol aştığından 260 karakterden artık throw bir <xref:System.IO.PathTooLongException?displayProperty=name> yalnızca aşağıdaki koşullar altında:<ul><li>Yol uzunluğunun büyüktür <xref:System.Int16.MaxValue> (32.767) karakter.</li><li>İşletim sistemi döndürür <code>COR_E_PATHTOOLONG</code> ya da eşdeğerine.</li></ul>.NET Framework 4.6.1 ve önceki sürümleri hedefleyen uygulamalar için çalışma zamanı otomatik olarak oluşturur bir <xref:System.IO.PathTooLongException?displayProperty=name> her bir yol 260 karakteri aşıyor.|
|Öneri|.NET Framework 4.6.2'yi hedefleyen uygulamalar için aşağıdaki ekleyerek arzu değil, uzun yol destek kapsamı dışında seçebilirsiniz <code>&lt;runtime&gt;</code> bölümünü, <code>app.config</code> dosyası:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Hedefleyen uygulamalar için .NET Framework'ün önceki sürümlerinde, ancak .NET Framework 4.6.2 çalıştırmak veya daha sonra uzun yol desteği için aşağıdaki ekleyerek kabul <code>&lt;runtime&gt;</code> bölümünü, <code>app.config</code> dosyası:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
