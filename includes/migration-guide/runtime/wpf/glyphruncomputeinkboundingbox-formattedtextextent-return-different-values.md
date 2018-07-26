### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a>.NET Framework 4. 5 ' başlayarak farklı değerler GlyphRun.ComputeInkBoundingBox() ve FormattedText.Extent döndürür

|   |   |
|---|---|
|Ayrıntılar|İyileştirmeler yapıldı <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> ve <xref:System.Windows.Media.FormattedText.Extent> burada kutuları bazı durumlarda .NET Framework 4.0 kapsanan karakter için çok küçük sorunlarını gidermek için .NET Framework 4.5 içinde. Bunun bir sonucu olarak, bazı sınırlama kutusu kullanıcı Arabirimi düzeninde farklar výsledek .NET Framework 4.5, daha büyük'den itibaren olacaktır.|
|Öneri|Bazı glif sınırlayıcı kutu boyutu artırmıştır dikkat edin. Bu değişiklikler, genellikle sunu ve isabet kutusunu test etme geliştirecek ancak eski (öncesi .NET 4.5) davranışı isterseniz, bunu app.config dosyasına şu giriş ekleyerek seçimi yaptıysanız:<pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|

