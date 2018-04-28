### <a name="certificate-eku-oid-validation"></a>Sertifika EKU OID ve doğrulama

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ile başlayan <xref:System.Net.Security.SslStream> veya <xref:System.Net.ServicePointManager> sınıfları Gelişmiş anahtar kullanımı (EKU) nesne tanımlayıcısı (OID) doğrulaması gerçekleştirin. Nesne tanımlayıcıları (OID) anahtarı kullanan uygulamalar belirtmek koleksiyonu bir Gelişmiş anahtar kullanımı (EKU) uzantısıdır. EKU OID doğrulama Uzak sertifika geri aramalar uzak sertifika amacı için doğru OID olduğundan emin olmak için kullanır.|
|Öneri|Bu değişiklik istenmeyen ise, sertifika EKU OID doğrulama aşağıdaki geçin ekleyerek devre dışı bırakabilirsiniz [ \<AppContextSwitchOverrides >](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) içinde [ ` ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) biri, Uygulama yapılandırma dosyası:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Bu ayar yalnızca geriye dönük uyumluluk için sağlanır. Aksi takdirde kullanımı önerilmez.</blockquote> |
|Kapsam|Küçük|
|Sürüm|4.6|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

