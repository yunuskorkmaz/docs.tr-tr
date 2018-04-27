### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>Bazı .NET API'lerini neden ilk fırsat (EntryPointNotFoundExceptions ele)

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 ilk fırsat atma .NET yöntemleri az sayıda başlangıcından <xref:System.EntryPointNotFoundException?displayProperty=name>s. Bu özel durumları .net içinde işlenen Framework, ancak ilk fırsat özel durum beklememeniz test Otomasyonu bozar. HighVersionLie etkinleştirilmişse, bu aynı API'leri bazı ApiVerifier senaryolar bölün.|
|Öneri|Bu hata, .NET Framework 4.5.1 yükselterek önlenebilir. Alternatif olarak, test Otomasyonu ilk fırsat üzerinde sonu olmayan güncelleştirilebilir <xref:System.EntryPointNotFoundException?displayProperty=name>s.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)?displayProperty=nameWithType></li></ul>|

