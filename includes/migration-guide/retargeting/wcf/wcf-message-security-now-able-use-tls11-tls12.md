### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>WCF ileti güvenliği artık TLS1.1 ve TLS1.2 kullanmaya devam edebilir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7 içinde başlayarak, müşterilerin TLS1.1 veya TLS1.2 uygulama yapılandırma ayarlarını aracılığıyla WCF ileti güvenliğini SSL3.0 ve TLS1.0 ek olarak yapılandırabilirsiniz.|
|Öneri|.NET Framework 4.7 TLS1.1 ve TLS1.2 WCF ileti güvenliği desteği varsayılan olarak devre dışıdır. Aşağıdaki satırı ekleyerek etkinleştirebilirsiniz <code>&lt;runtime&gt;</code> app.config veya web.config dosyasının:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Yeniden hedefleme|

