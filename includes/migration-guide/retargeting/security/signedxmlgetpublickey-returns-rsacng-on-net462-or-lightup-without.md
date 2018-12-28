### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml.GetPublicKey RSACng net462 (veya yerelleştirilmesi) değişiklik yeniden hedefleme olmadan döndürür

|   |   |
|---|---|
|Ayrıntılar|Tarafından döndürülen nesne somut türü .NET Framework 4.6.2 sürümünden itibaren <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> yöntemi bir Cng uygulamasına CryptoServiceProvider uygulamasından (quirk) değiştirildi. Uygulama kullanımından değiştiğinden budur <code>certificate.PublicKey.Key</code> iç kullanarak <code>certificate.GetAnyPublicKey</code> için iletir <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.|
|Öneri|.NET Framework 4.7.1 üzerinde çalışan uygulamalar ile başlayarak, varsayılan olarak .NET Framework 4.6.1 kullanılan CryptoServiceProvider uygulaması kullanabilirsiniz ve önceki sürümleri, aşağıdaki yapılandırma ekleyerek geçin [çalışma zamanı](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md), uygulama yapılandırma dosyası bölümünü:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType></li></ul>|

