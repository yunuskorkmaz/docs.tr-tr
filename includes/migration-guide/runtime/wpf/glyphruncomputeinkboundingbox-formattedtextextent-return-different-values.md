### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-45"></a>GlyphRun.ComputeInkBoundingBox() ve FormattedText.Extent .NET 4.5 başlayan farklı değerleri döndürür

|   |   |
|---|---|
|Ayrıntılar|Geliştirmeler yapıldı <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> ve <xref:System.Windows.Media.FormattedText.Extent> nerede kutuları .NET Framework 4.0 bazı durumlarda içerilen metindeki için çok küçük sorunları gidermek için .NET Framework 4.5 içinde. Bunun sonucunda, bazı sınırlayıcı kutularını UI düzeni küçük farklılıklar sonuçta .NET Framework 4.5, büyük'den itibaren olacaktır.|
|Öneri|Bazı karakter sınırlayıcı kutu boyutu artırmıştır unutmayın. Bu değişiklikler genellikle sunu ve isabet kutusunu test etme artırır, ancak eski (ön .NET 4.5) davranışı isterseniz bunu içine app.config dosyasına aşağıdaki giriş ekleyerek seçti:<pre><code class="language-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|

