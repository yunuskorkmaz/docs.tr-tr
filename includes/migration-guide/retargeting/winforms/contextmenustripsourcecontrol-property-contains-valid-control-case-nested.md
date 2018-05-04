### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a>İç içe geçmiş Toolstripmenuıtems durumunda geçerli bir denetim ContextMenuStrip.SourceControl özelliği içerir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ve önceki sürümlerde, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> yanlış içe menüden kullanıcı oturum açtığında döndürür null özelliği <xref:System.Windows.Forms.ToolStripMenuItem> kontrol eder. .NET Framework'teki 4.7.2 ve daha sonra <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> özelliği için gerçek kaynak denetimi her zaman ayarlayın.|
|Öneri|<strong>İçinde veya dışında bu değişiklikleri kabul etmek nasıl</strong>sırada bu değişikliklerden yararlanmak bir uygulama için .NET Framework 4.7.2 çalıştırmanız gerekir ya da daha sonra. Uygulama, aşağıdaki iki yoldan biriyle bu değişiklikleri yararlı olabilir:<ul><li>.NET Framework 4.7.2 hedefler. Bu, .NET Framework 4.7.2 hedef Windows Forms uygulamaları varsayılan olarak etkin veya üzeri değişikliktir.</li><li>.NET Framework 4.7.1 veya önceki bir sürümünü hedefler ve aşağıdakileri ekleyerek dışında eski erişilebilirlik davranışları çevrilir [AppContext anahtar](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) için <code>&lt;runtime&gt;</code> app.config dosyasını ve içinayarıbölümünü<code>false</code>, aşağıdaki örnekte gösterildiği gibi.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework 4.7.2 hedefleyen uygulamalar veya sonraki bir sürümü ve eski korumak istediğiniz davranışı kabul etme eski tip bir kaynak denetimi değeri kullanmak için bu AppContext anahtarı açıkça ayarlayarak <code>true</code>.|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType></li></ul>|

