### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>"dataAnnotations:dataTypeAttribute:disableRegEx" uygulama ayarı varsayılan olarak .NET Framework 4.7.2 açıktır

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.1, bir uygulama ayarı (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) sunulan veri türü öznitelikleri normal ifadelerde kullanımını devre dışı bırakmak kullanıcıların sağlar (gibi <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>, ve <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>). Bu, belirli normal ifadeler kullanarak bir hizmet reddi saldırısı olasılığı önleme gibi güvenlik açığı azaltılmasına yardımcı olur.<br/>.NET Framework 4.6.1, RegEx kullanımını devre dışı bırakmak için bu uygulama ayarı ayarlandı <code>false</code> varsayılan olarak. .NET Framework 4.7.2 ile başlamanızı, bu yapılandırma anahtarı ayarlandığında <code>true</code> daha da güvenli güvenlik açığı .NET Framework 4.7.2 hedef web uygulamaları için ve yukarıdaki azaltmak için varsayılan olarak.|
|Öneri|.NET Framework 4.7.2 yükselttikten sonra web uygulamanızda normal ifadeler çalışmıyor bulursanız, değerini güncelleştirebilirsiniz <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> ayarını <code>false</code> önceki davranışa geri dönmek için.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appsettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appsettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.2|
|Tür|Çalışma zamanı|

