### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>Varsayılan SignedXML ve SignedXMS algoritmaları için SHA256 değiştirildi

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7 ve önceki sürümleri için SHA1 SignedXML ve SignedCMS bazı işlemleri için varsayılan. .NET Framework 4.7.1 ile başlayarak, SHA256, bu işlemler için varsayılan olarak etkindir. Bu değişiklik, SHA1 artık güvenli olarak kabul edilir çünkü gereklidir.|
|Öneri|Varsayılan olarak SHA1 (güvenli) veya SHA256 kullanılıp kullanılmadığını denetlemek için iki yeni bağlam anahtar değer vardır:<ul><li>Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</li><li>Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms</li></ul>SHA256 kullanımını istenmeyen, ise hedef .NET Framework 4.7.1 ve sonraki sürümlerde, varsayılan SHA1 için aşağıdaki yapılandırma ekleyerek geri yükleyebilirsiniz, uygulamalar için geçin [çalışma zamanı](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) , uygulama yapılandırma bölümü Dosya:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true&quot; /&gt;&#13;&#10;</code></pre>.NET Framework 4.7 ve önceki sürümleri hedefleyen uygulamalar için aşağıdaki yapılandırma anahtarı için ekleyerek bu değişikliği veritabanına seçebilirsiniz [çalışma zamanı](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) , uygulama yapılandırma dosyası bölümünü:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType></li></ul>|

