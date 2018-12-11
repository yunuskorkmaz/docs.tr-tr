### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>Dizeler gömülü null değerlere sahip EventListener keser

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> dizeler gömülü null değerlere sahip keser. Boş karakterler tarafından desteklenmez <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> sınıfı. Bu değişiklik yalnızca kullanan uygulamaları etkiler <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> okunacak <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> işlemdeki veri ve sınırlayıcı olarak null karakterleri kullanın.|
|Öneri|<xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> Veri mümkün olduğunda, gömülü null karakterleri kullanmayacak şekilde güncelleştirilmelidir.|
|Kapsam|Kenar|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|

