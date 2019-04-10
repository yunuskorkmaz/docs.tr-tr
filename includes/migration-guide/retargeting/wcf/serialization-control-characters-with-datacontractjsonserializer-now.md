---
ms.openlocfilehash: 0642b184d85306a453d429f247dad95a259cb012
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236574"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>DataContractJsonSerializer ile denetim karakterlerini serileştirilmesi artık ECMAScript V6 ve V8 uyumludur

|   |   |
|---|---|
|Ayrıntılar|.NET framework 4.6.2 ve önceki sürümlerinde, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> \b \f ve ECMAScript V6 ve V8 standartları ile uyumlu bir şekilde \t gibi bazı özel denetim karakterleri serileştirilecek değil. .NET Framework 4.7 ile başlayarak, bu denetim karakterleri serileştirilmesi V8 ECMAScript V6 ile uyumludur.|
|Öneri|.NET Framework 4.7 hedefleyen uygulamalar için bu özellik varsayılan olarak etkindir. Bu davranış arzu değil ise, aşağıdaki satırı ekleyerek bu özelliği seçebilirsiniz <code>&lt;runtime&gt;</code> app.config veya web.config dosyasının:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|
