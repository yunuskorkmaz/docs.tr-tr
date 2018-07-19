### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Bazı .NET SDK Araçları için geliştirilmiş erişilebilirlik

|   |   |
|---|---|
|Ayrıntılar|.NET Framework SDK içinde 4.7.1 SvcConfigEditor.exe ve SvcTraceViewer.exe Araçlar çeşitli erişilebilirlik sorunları çözme tarafından geliştirilmiştir. Bunların çoğu tanımlanmayan bir ad veya doğru uygulanmadı belirli bir UI Otomasyon düzenleri gibi küçük problemler yoktu. Çok sayıda kullanıcı yanlış bu değerlerin farkında olmaz mıydı ancak ekran okuyucular gibi yardımcı teknolojiler kullanan müşteriler bu SDK Araçları daha erişilebilir bulabilirsiniz. Elbette bu düzeltmeler klavye odağı sırası gibi önceki bazı davranışları değiştirir. Tüm bu araçlarda erişilebilirlik düzeltmeleri almak için app.config dosyanıza aşağıdakileri yapabilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7.1|
|Tür|Yeniden hedefleme|

