---
ms.openlocfilehash: 506218195417548880a9d8d10508a570a7769682
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859317"
---
### <a name="long-path-support"></a>Uzun yol desteği

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2'yi hedefleyen uygulamalardan başlayarak, uzun yollar (32K karaktere kadar) desteklenir <code>MAX_PATH</code>ve yol uzunluklarındaki 260 karakterlik (veya) sınırlaması kaldırılmıştır. .NET Framework 4.6.2'yi hedeflemek için yeniden derlenen uygulamalar için, daha önce <xref:System.IO.PathTooLongException?displayProperty=name> 260 karakteri aşan <xref:System.IO.PathTooLongException?displayProperty=name> bir yol attığı kod yolları artık yalnızca aşağıdaki koşullar altında bir yol açacaktır:<ul><li>Yolun uzunluğu (32.767) karakterden <xref:System.Int16.MaxValue> daha büyüktür.</li><li>İşletim sistemi <code>COR_E_PATHTOOLONG</code> veya eşdeğeri döndürür.</li></ul>.NET Framework 4.6.1 ve önceki sürümleri hedefleyen uygulamalar için çalışma <xref:System.IO.PathTooLongException?displayProperty=name> süresi, bir yol 260 karakteri aştığında otomatik olarak atar.|
|Öneri|.NET Framework 4.6.2'yi hedefleyen uygulamalar için, dosyanızın <code>&lt;runtime&gt;</code> <code>app.config</code> bölümüne aşağıdakileri ekleyerek uzun yol desteğini devre dışı kullanabilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework'ün önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya sonraki sürümlerde çalışan uygulamalar için, <code>&lt;runtime&gt;</code> dosyanızın <code>app.config</code> bölümüne aşağıdakileri ekleyerek uzun yol desteğini tercih edebilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
