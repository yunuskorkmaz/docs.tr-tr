### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>Aynı aldığı parametreleri (artı kimliği) EventSource.WriteEvent impls WriteEvent geçmelidir

|   |   |
|---|---|
|Ayrıntılar|Çalışma Zamanı artık aşağıdaki belirten sözleşmenin uygular: öğesinden türetilmiş bir sınıf <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> tanımlayan bir ETW olay yöntemi temel sınıf çağırmalıdır <code>EventSource.WriteEvent</code> olay kimliği yöntemiyle ETW olay yöntemi aynı bağımsız değişkenleri tarafından izlenen geçirildi.|
|Öneri|Bir <xref:System.IndexOutOfRangeException?displayProperty=name> , özel durum bir <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> okur <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> bu sözleşmeyi ihlal eden bir olay kaynağı için işlem verileri.|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|

