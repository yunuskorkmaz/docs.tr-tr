### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml.GetPublicKey RSACng net462 (veya yerelleştirilmesi) değişiklik yeniden hedefleme olmadan döndürür

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2, somut tarafından döndürülen nesne türünü başlayarak <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> yöntemi CryptoServiceProvider uygulamasından (quirk) bir Cng uygulama değiştirildi. Uygulamasını kullanarak değiştiğinden budur <code>certificate.PublicKey.Key</code> iç kullanmanın <code>certificate.GetAnyPublicKey</code> için ileten <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.|
|Öneri|.NET Framework 4.7.1 çalışan uygulamaları ile başlayarak, .NET Framework 4.6.1 varsayılan olarak kullanılan CryptoServiceProvider uygulaması kullanabilirsiniz ve aşağıdaki yapılandırma ekleyerek önceki sürümlerinde geçin [çalışma zamanı](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md)uygulama yapılandırma dosyası bölümünü:<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.6.2|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType></li></ul>|

