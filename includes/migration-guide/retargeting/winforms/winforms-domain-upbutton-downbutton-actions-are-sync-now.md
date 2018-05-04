### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a>WinForm'ın etki alanı upbutton ve downbutton eylemler şimdi eşitleme

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ve önceki sürümlerinde <xref:System.Windows.Forms.DomainUpDown> denetimin <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> denetimi metin mevcut olduğunda ve geliştirici kullanmak için gereken eylemi görmezden <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> Denetimi kullanmadan önce eylem <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> eylem. 4.7.2 hem .NET Framework ile başlayan <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> eylemleri bağımsız olarak bu senaryoda, iş ve eşit olarak kalır.|
|Öneri|Sırayla bu değişikliklerden yararlanmak bir uygulama için .NET Framework 4.7.2 çalıştırmanız gerekir ya da daha sonra. Uygulama, aşağıdaki iki yoldan biriyle bu değişiklikleri yararlı olabilir:<ul><li>.NET Framework 4.7.2 hedeflemek için derlenmiştir. Bu, .NET Framework 4.7.2 hedef Windows Forms uygulamaları varsayılan olarak etkin veya üzeri değişikliktir.</li><li>Aşağıdakileri ekleyerek davranışı kaydırma eski dışında çevrilir [AppContext anahtar](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) için <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyasını ve ayarlamak bölümünü <code>false</code>, aşağıdaki örnekte gösterildiği gibi.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType></li><li><xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType></li></ul>|

