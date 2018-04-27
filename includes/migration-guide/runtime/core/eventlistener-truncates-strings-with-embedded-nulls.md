### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>Katıştırılmış null değerlere dizelerle EventListener keser

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> Katıştırılmış null değerlere dizelerle tamsayıya dönüştürür. Boş karakterler tarafından desteklenmeyen <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> sınıfı. Değişiklik yalnızca kullanan uygulamaları etkiler <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> okumak için <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> işleminde veri ve, sınırlayıcı olarak boş karakterler kullanın.|
|Öneri|<xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> Veri Mümkünse, katıştırılmış boş karakterler kullanmayacak şekilde güncelleştirilmelidir.|
|Kapsam|Kenar|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|

