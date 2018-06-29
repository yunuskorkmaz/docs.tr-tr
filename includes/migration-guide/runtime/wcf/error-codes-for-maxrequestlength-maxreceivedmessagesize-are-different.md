### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a>Hata kodları maxRequestLength veya maxReceivedMessageSize farklı

|   |   |
|---|---|
|Ayrıntılar|WCF iletilerinde web maxRequestLength (gelen ASP.NET) aşan Internet Information Services (IIS) veya ASP.NET Geliştirme Sunucusu barındırılan hizmetleri veya maxReceivedMessageSize (WCF)'de sahip farklı hata değişkenden HTTP durum kodu 400 (Hatalı istek değişti ) 413 (istek varlığı çok büyük) ve maxRequestLength veya maxReceivedMessageSize ayarı aşan iletileri throw bir <xref:System.ServiceModel.ProtocolException?displayProperty=name> özel durum. Bu aktarım modu akışı durumlarda içerir.|
|Öneri|Bu değişiklik, burada ileti ASP.NET veya WCF tarafından izin verilen sınırı aşıyor durumlarda hata ayıklama kolaylaştırır. Bir HTTP 400 durum koduna göre işleyen herhangi bir kodu değiştirmeniz gerekir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|çalışma zamanı|

