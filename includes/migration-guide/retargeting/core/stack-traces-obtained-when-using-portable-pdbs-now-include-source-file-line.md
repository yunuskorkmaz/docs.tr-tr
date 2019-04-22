---
ms.openlocfilehash: 384f8c7fa08b69c13d05edb3404787d428dad837
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774107"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a>Taşınabilir pdb artık kullanırken alınan yığın izlemelerini istenirse kaynak dosya ve satır bilgileri içerir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ile başlayarak, yığın izlemelerini taşınabilir pdb kullanırken alınan istendiğinde kaynak dosya ve satır bilgileri içerir. .NET Framework 4.7.2, kaynak dosya ve satır'dan önceki sürümlerde bilgi taşınabilir pdb açıkça istenmiş olsa bile kullanırken kullanılamaz olacaktır.|
|Öneri|.NET Framework'ü 4.7.2 hedefleyen uygulamalar için kaynak dosya ve satır bilgileri dışında aşağıdaki ekleyerek arzu değil, taşınabilir pdb kullanırken seçebilirsiniz <code>&lt;runtime&gt;</code> bölümünü, <code>app.config</code> dosyası:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Hedefleyen uygulamalar için .NET Framework'ün önceki sürümlerinde .NET Framework 4.7.2 ancak çalıştırmak veya daha sonra kaynak dosya ve satır bilgileri için taşınabilir pdb aşağıdakileri ekleyerek kullanırken kabul <code>&lt;runtime&gt;</code> , bölümünü<code>app.config</code>dosyası:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)?displayProperty=nameWithType><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)?displayProperty=nameWithType></li></ul>|
