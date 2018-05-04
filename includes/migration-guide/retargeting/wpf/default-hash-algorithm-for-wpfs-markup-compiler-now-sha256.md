### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>WPF'ın biçimlendirme derleyici için varsayılan karma algoritma SHA256 sunulmuştur

|   |   |
|---|---|
|Ayrıntılar|WPF MarkupCompiler XAML işaretleme dosyaları için derleme hizmetleri sağlar.  .NET Framework 4.7.1 ve önceki sürümlerinde sağlaması için kullanılan varsayılan karma algoritma SHA1 oluştu. SHA1 ile en son güvenlik sorunları nedeniyle bu varsayılan değer SHA256 için değiştirildi .NET Framework ile 4.7.2 başlatılıyor.  Bu değişiklik, derleme sırasında biçimlendirme dosyaları için tüm sağlama toplamı oluşturmayı etkiler.|
|Öneri|.NET Framework 4.7.2 hedefleyen bir geliştirici veya daha büyük ve istediği SHA1 karma davranışa geri dönmek için aşağıdaki AppContext bayrağı ayarlamanız gerekir.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Aşağıda 4.7.2 .NET framework sürümünü hedefleme ayarlamalısınız sırada SHA256 karma kullanmak isteyen bir geliştirici AppContext bayrağı aşağıda.  .NET Framework'ün yüklü olan sürüm 4.7.2 olmasına dikkat edin veya daha büyük.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Geçirgen|
|Sürüm|4.7.2|
|Tür|Yeniden hedefleme|

