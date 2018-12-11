### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>WCF MsmqSecureHashAlgorithm varsayılan değer SHA256 şimdi:

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ile başlayarak, imza algoritması wcf'de Msmq iletileri için varsayılan SHA256 iletisidir. .NET Framework 4.7 ve önceki sürümleri, imza algoritması varsayılan ileti SHA1 ' dir.|
|Öneri|.NET Framework 4.7.1 uyumluluk sorunları bu değişikliği halinde çalıştırın ya da daha sonra değişikliğin aşağıdaki satırı ekleyerek çevirme <code>&lt;runtime&gt;</code>app.config dosyanıza bölümünü:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.1|
|Tür|Çalışma zamanı|

