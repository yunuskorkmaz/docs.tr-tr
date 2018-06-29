### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>EventSource.WriteEvent impls WriteEvent aynı aldığı parametreleri (artı kimliği) geçmelidir

|   |   |
|---|---|
|Ayrıntılar|Çalışma zamanı şimdi aşağıdaki belirtir sözleşme zorlar: öğesinden türetilmiş bir sınıf <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> bir ETW tanımlayan olay yöntemi temel sınıf çağırmalıdır <code>EventSource.WriteEvent</code> olay kimliği yöntemiyle ETW olay yöntemi aynı bağımsız değişkenlere tarafından izlenen geçirildi.|
|Öneri|Bir <xref:System.IndexOutOfRangeException?displayProperty=name> , özel durum bir <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> okur <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> işlemi bu sözleşmeyi ihlal eden bir olay kaynağı için verileri.|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|çalışma zamanı|

