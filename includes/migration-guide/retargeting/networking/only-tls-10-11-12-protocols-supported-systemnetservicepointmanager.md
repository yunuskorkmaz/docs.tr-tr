### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>Yalnızca System.Net.ServicePointManager ve System.Net.Security.SslStream desteklenen Tls 1.0, 1.1 ve 1.2 protokolleri

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ile başlayan <xref:System.Net.ServicePointManager> ve <xref:System.Net.Security.SslStream> sınıfları aşağıdaki üç protokolden birini kullanmak için izin verilmez: Tls1.0, Tls1.1 veya Tls1.2. RC4 şifreleme ve SSL3.0 protokolü desteklenmiyor.|
|Öneri|Önerilen risk azaltma Tls1.0, Tls1.1 ya da Tls1.2 için sunucu tarafı uygulama yükseltmektir. Bu uygun olmadığı veya istemci uygulamaları koptu <xref:System.AppContext?displayProperty=name> sınıfı, bu özellik iki yoldan biriyle dışında kabul etmek için kullanılabilir:<ol><li>Compat anahtarlarını programlı olarak ayarlayarak <xref:System.AppContext?displayProperty=name>açıklandığı gibi [burada](http://blogs.msdn.com/b/dotnet/archive/2015/04/29/net-announcements-at-build-2015.aspx#dotnet46)</li><li>Aşağıdaki satırı ekleyerek <code>&lt;runtime&gt;</code> app.config dosyasının: <code>&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSchUseStrongCrypto=true&quot;/&gt;</code>;</li></ol>|
|Kapsam|Küçük|
|Sürüm|4.6|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType></li></ul>|

