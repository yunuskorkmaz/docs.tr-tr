### <a name="tls-1x-by-default-passes-the-schsendauxrecord-flag-to-the-underlying-schannel-api"></a>TLS 1.x varsayılan olarak temel alınan SCHANNEL API'sine SCH_SEND_AUX_RECORD bayrağı geçirir

|   |   |
|---|---|
|Ayrıntılar|TLS kullanırken 1.x, .NET Framework üzerinde temel alınan Windows SCHANNEL API kullanır. .NET Framework 4.6 ile başlayan [SCH_SEND_AUX_RECORD](https://msdn.microsoft.com/library/windows/desktop/aa379810.aspx) bayrağı SCHANNEL için varsayılan olarak geçirilir. Bu verilerin iki ayrı kayıt, ilk olarak bir tek baytlı ve ikinci olarak içine şifrelenmesi için bölme SCHANNEL neden <em>n</em>-1 bayt. Nadir durumlarda, bu istemciler ve verileri tek bir kayıtta bulunduğu olduğu varsayımını yaparsınız varolan sunucular arasındaki iletişimi keser.|
|Öneri|Bu değişiklik var olan bir sunucu ile iletişim bozarsa, gönderme devre dışı bırakabilirsiniz [SCH_SEND_AUX_RECORD](https://msdn.microsoft.com/library/windows/desktop/aa379810.aspx) bayrak ve veri ayrı ayrı kayıtlara aşağıdaki anahtara ekleyerek bölme değil, önceki davranışını geri yükleme [ <AppContextSwitchOverrides> ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ <runtime> ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyası bölümünü:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Bu ayar yalnızca geriye dönük uyumluluk için sağlanır. Aksi takdirde kullanımı önerilmez.</blockquote> |
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

