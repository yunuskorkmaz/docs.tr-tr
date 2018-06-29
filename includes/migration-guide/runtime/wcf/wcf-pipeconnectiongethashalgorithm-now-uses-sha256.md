### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>WCF PipeConnection.GetHashAlgorithm artık SHA256 kullanır

|   |   |
|---|---|
|Ayrıntılar|Windows Communication Foundation .NET Framework 4.7.1 ile başlayarak, adlandırılmış kanallar için rastgele adlar oluşturmak için SHA256 karma kullanır. .NET Framework 4.7 ve önceki sürümleri, SHA1 karma kullanılır.|
|Öneri|.NET Framework 4.7.1 uyumluluk sorunu bu değişikliği içine çalıştırın ya da daha sonra bunu aşağıdaki satırı ekleyerek çevirin <code>&lt;runtime&gt;</code> app.config dosyasının:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.1|
|Tür|çalışma zamanı|

