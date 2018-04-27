### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>ETW olay adları yalnızca "Başlat" veya "Durdur" soneki ile farklı olamaz

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ve 4.6.1, çalışma zamanı oluşturur bir <xref:System.ArgumentException> iki olay Windows için izleme (ETW) olayı adları farklı yalnızca ne zaman bir &quot;Başlat&quot; veya &quot;durdurmak&quot; soneki (bir olay zamanadlıolarak<code>LogUser</code>ve başka bir adlandırılmış <code>LogUserStart</code>). Bu durumda, çalışma zamanı tüm günlük yayılamıyor olay kaynağı oluşturulamaz.|
|Öneri|Özel durum önlemek için iki olay adları yalnızca göre farklılık olun bir &quot;Başlat&quot; veya &quot;durdurmak&quot; soneki. Bu gereksinim .NET Framework 4.6.2 ile başlayan kaldırılır; çalışma zamanı yalnızca farklı olay adlarını ayırt etmek &quot;Başlat&quot; ve &quot;durdurmak&quot; soneki.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Yeniden hedefleme|

