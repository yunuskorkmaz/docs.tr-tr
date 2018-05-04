### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>DataContractJsonSerializer ile bir denetim karakteri serileştirmek şimdi ECMAScript V6 ve V8 uyumludur

|   |   |
|---|---|
|Ayrıntılar|.NET framework 4.6.2 ve önceki sürümlerde, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> \b, \f ve ECMAScript V6 ve V8 standartlarla uyumlu bir şekilde \t gibi bazı özel denetim karakterleri seri değildir. .NET Framework 4.7 ile başlayarak, bu denetim karakterleri serileştirmek ECMAScript V6 ve V8 ile uyumludur.|
|Öneri|.NET Framework 4.7 hedef uygulamaları için bu özellik varsayılan olarak etkindir. Bu davranış arzu değilse, aşağıdaki satırı ekleyerek dışında bu özellik seçebilirsiniz <code>&lt;runtime&gt;</code> app.config veya web.config dosyasının:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|

