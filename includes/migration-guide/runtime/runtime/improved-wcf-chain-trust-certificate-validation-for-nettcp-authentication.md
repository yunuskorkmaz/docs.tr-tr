### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>Geliştirilmiş WCF zinciri güven sertifikası doğrulama Net.Tcp sertifika kimlik doğrulaması

|   |   |
|---|---|
|Ayrıntılar|.NET framework 4.7.2 zinciri güven sertifikası doğrulama sertifikası kimlik doğrulaması WCF ile taşıma güvenliği ile kullanırken artırır. Bu geliştirme ile bir sunucuya kimlik doğrulaması için kullanılan istemci sertifikalarını istemci kimlik doğrulaması için yapılandırılmış olması gerekir.  Benzer şekilde bir sunucu kimlik doğrulaması için sunucu sertifikaları sunucu kimlik doğrulaması için yapılandırılmış olması gerekir. Kök sertifikayı devre dışıysa, bu değişiklikle, sertifika zinciri doğrulaması başarısız olur. Aynı değişiklik de .NET Framework 3.5 ve sonraki sürümlerinde Windows Güvenliği aracılığıyla dökümü çalışıldı. Daha fazla bilgi bulabilirsiniz [burada](https://support.microsoft.com/en-us/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Bu değişiklik, varsayılan olarak açıktır ve bir yapılandırma ayarı tarafından devre dışı bırakılabilir.|
|Öneri|<ul><li>Sunucu ve istemci sertifika gerekli EKU OID olup olmadığını doğrulayın. Aksi durumda, sertifikanızı güncelleştirin.</li><li>Kök sertifika geçersiz olduğunda doğrulayın. Bu durumda, kök sertifikayı güncelleştirin.</li><li>Değişiklik dışında kabul etme: sertifika güncelleştirilemiyor, geçici olarak önemli değişiklik şu yapılandırma ayarı ile çalışabilir, ancak değişiklik dışında kullanmama sisteminizi güvenlik sorundan bırakır.</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.2|
|Tür|Çalışma zamanı|

