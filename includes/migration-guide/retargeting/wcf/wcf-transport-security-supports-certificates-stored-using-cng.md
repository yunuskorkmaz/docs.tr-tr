### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>WCF taşıma güvenliği CNG kullanarak depolanan sertifika destekler

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 hedefleyen uygulamalar ile başlayarak, WCF taşıma güvenliği Windows şifreleme kitaplığı (CNG) kullanarak depolanan sertifikalar destekler. Bu destek sertifikaları üs en fazla 32 bit uzunlukta bir ortak anahtar ile sınırlıdır. Bir uygulamayı .NET Framework 4.6.2 hedeflediğinde, bu özellik varsayılan olarak açıktır. .NET Framework önceki sürümlerde X509 kullanma girişimi CSG ile sertifika anahtarı depolama sağlayıcısı bir özel durum oluşturur.|
|Öneri|.NET Framework 4.6.2 hedef .NET Framework 4.6.1 ve önceki ancak çalışan uygulamalar, aşağıdaki satırı ekleyerek CNG sertifikalarından desteği etkinleştirebilir <code>&lt;runtime&gt;</code> app.config veya web.config dosyasının:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableCngCertificates=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Bu ayrıca programlı olarak aşağıdaki kod ile yapılabilir:<pre><code class="lang-cs">private const string DisableCngCertificates = @&quot;Switch.System.ServiceModel.DisableCngCertificate&quot;;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, false);&#13;&#10;</code></pre><pre><code class="lang-vb">Const DisableCngCertificates As String = &quot;Switch.System.ServiceModel.DisableCngCertificates&quot;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, False)&#13;&#10;</code></pre>Bu değişikliği nedeniyle hiçbir özel durum işleme girişimi başarısız olmasına CNG sertifikayla güvenli iletişim başlatmak için bağımlı kodunu artık yürütecek olduğunu unutmayın.|
|Kapsam|Küçük|
|Sürüm|4.6.2|
|Tür|Yeniden hedefleme|

