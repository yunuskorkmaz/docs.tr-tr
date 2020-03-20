---
ms.openlocfilehash: 2c532bf3778b940f68db859420dd12826e9da388
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77466086"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>DataContractJsonSerializer ile kontrol karakterlerinin serileştirilmesi artık ECMAScript V6 ve V8 ile uyumludur

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ve önceki <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> sürümlerde, \b, \f ve \t gibi bazı özel denetim karakterlerini ECMAScript V6 ve V8 standartlarıyla uyumlu bir şekilde serihale getiremedi. .NET Framework 4.7 ile başlayarak, bu kontrol karakterlerinin serileştirilmesi ECMAScript V6 ve V8 ile uyumludur.|
|Öneri|.NET Framework 4.7'yi hedefleyen uygulamalar için bu özellik varsayılan olarak etkinleştirilir. Bu davranış istenmiyorsa, app.config veya web.config dosyasının <code>&lt;runtime&gt;</code> bölümüne aşağıdaki satırı ekleyerek bu özelliği devre dışı kullanabilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Edge|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|
