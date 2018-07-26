### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a>Hata kodları maxRequestLength veya maxReceivedMessageSize için farklıdır

|   |   |
|---|---|
|Ayrıntılar|Wcf'de ileti web maxRequestLength (ASP.NET'te) aşan Internet Information Services (IIS) veya ASP.NET Development Server'da barındırılan hizmetleri veya maxReceivedMessageSize (wcf'de) sahip farklı hata değişkenden HTTP durum kodu 400 (Hatalı istek değişti ) iken 413 (istek varlığı çok büyük) ve maxRequestLength veya maxReceivedMessageSize ayarını aşan iletiler throw bir <xref:System.ServiceModel.ProtocolException?displayProperty=name> özel durum. Bu, aktarım modunun akış yoluyla servis taleplerini içerir.|
|Öneri|Bu değişiklik, burada ileti uzunluğu ASP.NET veya WCF tarafından izin verilen sınırları aştığı durumlarda hata ayıklamayı kolaylaştırır. Bir HTTP 400 durum koduna göre işleyen herhangi bir kodu değiştirmeniz gerekir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|

