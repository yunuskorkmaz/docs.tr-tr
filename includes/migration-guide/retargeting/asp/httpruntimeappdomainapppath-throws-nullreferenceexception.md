### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>NullReferenceException HttpRuntime.AppDomainAppPath oluşturur

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2'da, çalışma zamanı oluşturur bir <code>T:System.NullReferenceException</code> alınırken bir <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> boş karakterler içeren değer. .NET Framework 4.6.1 ve önceki sürümleri, çalışma zamanı oluşturur bir <code>T:System.ArgumentNullException</code>.|
|Öneri|Bu değişiklik yanıt izleme birini yapabilirsiniz:<ul><li>Tanıtıcı <code>T:System.NullReferenceException</code> uygulama, .NET Framework 4.6.2 çalıştırıyorsa.</li><li>Önceki davranışını geri yükler ve oluşturur .NET Framework 4.7, yükseltme bir <code>T:System.ArgumentNullException</code>.</li></ul>|
|Kapsam|Kenar|
|Sürüm|4.6.2|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|

