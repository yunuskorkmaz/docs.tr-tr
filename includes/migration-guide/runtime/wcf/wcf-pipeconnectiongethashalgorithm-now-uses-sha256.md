### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>WCF PipeConnection.GetHashAlgorithm SHA256 artık kullanır.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ile başlayarak, Windows Communication Foundation SHA256 karma rastgele adları için adlandırılmış kanallar oluşturmak için kullanır. .NET Framework 4.7 ve önceki sürümlerinde SHA1 karması kullanılır.|
|Öneri|.NET Framework 4.7.1 Bu değişiklik ile uyumluluk sorunu içine çalıştırın ya da daha sonra bunu aşağıdaki satırı ekleyerek çevirme <code>&lt;runtime&gt;</code> app.config dosyanıza bölümünü:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.1|
|Tür|Çalışma zamanı|

