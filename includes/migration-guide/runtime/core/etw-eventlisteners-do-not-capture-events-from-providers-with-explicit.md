### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>ETW EventListeners (gibi TPL sağlayıcısı) açık sözcüklerle sağlayıcılardan gelen olayları yakalamak değil

|   |   |
|---|---|
|Ayrıntılar|ETW EventListeners boş anahtar sözcüğü maskesiyle düzgün açık sözcüklerle sağlayıcılardan olayları yakalar değil. .NET Framework 4.5 TPL sağlayıcısı açık anahtar sözcükleri sağlama başladı ve bu sorunu tetiklendi. .NET Framework 4.6 EventListeners artık bu sorunu sağlamak için güncelleştirilmiştir.|
|Öneri|Bu sorunu geçici olarak çözmek için çağrıları yerini <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> açıkça belirtir EnableEvents aşırı çağrıları ile &quot;herhangi bir anahtar sözcük&quot; kullanılacak maskesi: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>. Alternatif olarak, bu sorun .NET Framework 4.6 sabit ve .NET Framework'ün bu sürüme yükseltme tarafından desteklenebilir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|

