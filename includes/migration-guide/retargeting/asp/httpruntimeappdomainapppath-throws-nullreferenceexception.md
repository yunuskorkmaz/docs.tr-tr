### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>NullReferenceException HttpRuntime.AppDomainAppPath oluşturur

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2, çalışma zamanı oluşturur bir <code>T:System.NullReferenceException</code> alınırken bir <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> null karakterleri içeren bir değer. .NET Framework 4.6.1 ve önceki sürümlerinde, çalışma zamanı oluşturur bir <code>T:System.ArgumentNullException</code>.|
|Öneri|Bu değişiklik yanıt vermek için izleme birini yapabilirsiniz:<ul><li>Tanıtıcı <code>T:System.NullReferenceException</code> uygulamanız .NET Framework 4.6.2 çalışıyorsa.</li><li>Önceki davranış geri yükler ve oluşturur .NET Framework 4.7, yükseltme bir <code>T:System.ArgumentNullException</code>.</li></ul>|
|Kapsam|Kenar|
|Sürüm|4.6.2|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|

