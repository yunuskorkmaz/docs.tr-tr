### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Application.FilterMessage IMessageFilter.PreFilterMessage a uygulamaları için artık oluşturur

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.1 öncesinde, arama <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> ile bir <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> çağırıldığı <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> veya <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> (Ayrıca çağırma sırasında <xref:System.Windows.Forms.Application.DoEvents>) neden olacağından bir <xref:System.IndexOutOfRangeException?displayProperty=name>. .NET Framework 4.6.1 hedefleyen uygulamalar ile başlayarak, bu özel durum artık oluşturulur ve içe filtreleri yukarıda açıklandığı gibi kullanılabilir.|
|Öneri|Unutmayın, <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> artık içe için özel durum oluşturacak <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> yukarıda açıklanan davranışı. Bu, yalnızca .NET Framework 4.6.1 dışında bu değişikliği kabul 4.6.1.Apps .NET Framework hedefleme (veya hedefleme eski çerçeveleri kabul etme uygulamalar) hedefleme uygulamaları kullanarak etkiler [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) Uyumluluk anahtarı.|
|Kapsam|Kenar|
|Sürüm|4.6.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|

