### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Bazı .NET SDK Araçları için gelişmiş Erişilebilirlik

|   |   |
|---|---|
|Ayrıntılar|.NET Framework SDK'ın 4.7.1, çeşitli erişilebilirlik sorunları düzelterek SvcConfigEditor.exe ve SvcTraceViewer.exe araçları geliştirilmiştir. Bunların çoğu tanımlı bir ad veya doğru şekilde uygulanan değil belirli UI Otomasyon düzenleri gibi küçük sorunları oluştu. Çok sayıda kullanıcı yanlış bu değerlerden farkında olmayacaktır olsa da, ekran okuyucular gibi yardımcı teknolojiler kullanan müşteriler bu SDK Araçları daha erişilebilir bulur. Bu düzeltmeler kesinlikle, klavye odağı sipariş gibi önceki bazı davranışları değiştirin. Tüm bu araçlar erişilebilirlik düzeltmeleri almak için app.config dosyasına aşağıdakileri yapabilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7.1|
|Tür|Yeniden hedefleme|

