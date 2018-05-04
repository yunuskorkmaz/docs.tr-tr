### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a>Klavye odağı artık doğru WinForms/WPF barındırma birden çok katmanda taşır

|   |   |
|---|---|
|Ayrıntılar|WPF denetimlerini sırayla barındıran bir WinForms denetimi barındırma WPF uygulaması göz önünde bulundurun. Kullanıcılar bu katmandaki ilk veya son denetim WPF ise dışında WinForms katman sekmesinde mümkün olmayabilir <code>System.Windows.Forms.Integration.ElementHost</code>. Bu değişiklik, bu sorunu giderir ve kullanıcılar artık dışında WinForms katman sekmesinde imkanınız olur. Hiçbir zaman WinForms katman kaçış odaklanmak kullanan otomatik uygulamalar artık beklendiği gibi çalışmayabilir.|
|Öneri|Aşağıda 4.7.2 .NET framework sürümünü hedefleme sırasında bu değişikliği kullanmak isteyen bir geliştirici, değişikliğin etkin false AppContext bayrakları aşağıdaki kümesini ayarlayabilirsiniz.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>WPF uygulamaları sonraki geliştirmeleri almak için tüm erken erişilebilirlik geliştirmeleri olarak mı etmeniz gerekir. Diğer bir deyişle, her ikisi de <code>Switch.UseLegacyAccessibilityFeatures</code> ve <code>Switch.UseLegacyAccessibilityFeatures.2</code> büyük can true değişikliğin devre dışı aşağıdaki AppContext bayrağı ayarlayın veya anahtarları .NET 4.7.2 hedefleme sırasında önceki işlevselliği gerektiren setA Geliştirici olmalıdır.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Yeniden hedefleme|

