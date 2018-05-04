### <a name="deflatestream-uses-native-apis-for-decompression"></a>DeflateStream yerel API'leri açma işlemi için kullanır.

|   |   |
|---|---|
|Ayrıntılar|4.7.2, .NET Framework içinde açma uyarlamasını başlayarak <code>T:System.IO.Compression.DeflateStream</code> sınıfı, varsayılan olarak yerel Windows API'ları kullanmak üzere değişti. Genellikle, bu bir önemli performans iyileştirme sonuçlanır. .NET Framework sürüm 4.7.2 veya daha yüksek kullanım yerel uygulama hedefleyen tüm .NET uygulamaları. Bu değişiklik dahil bazı farklılıklar davranışı, neden olabilir:<ul><li>Özel durum iletileri farklı olabilir. Ancak, özel durum türü aynı kalır.</li><li>Bir işlemi tamamlamak için yeterli bellek olmaması gibi bazı özel durumlarda farklı şekilde ele alınabilir.</li><li>Gzip üstbilgi ayrıştırması farklar bilinen vardır (Not: yalnızca <code>GZipStream</code> açma etkilenen ayarlayın):</li><li>Farklı zamanlarda geçersiz üstbilgileri ayrıştırılırken özel durum.</li><li>Yerel uygulama için bazı değerler bayrakları gzip üstbilgisi içinde ayrılmış zorlar (yani [süre](http://www.zlib.org/rfc-gzip.html#header-trailer)) burada geçersiz değerler önceden yoksayıldı bir özel durum neden belirtimine göre ayarlanır.</li></ul>|
|Öneri|Açma işlemi sırasında yerel API'leri ile uygulamanızı davranışını olumsuz etkilediğini, ekleyerek dışında bu özellik seçebilirsiniz <code>Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression</code> geçiş <code>runtime</code> , app.config dosyası ve ayarlamak bölümünü <code>true</code>:<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot; ?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.2|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType></li><li><xref:System.IO.Compression.GZipStream?displayProperty=nameWithType></li></ul>|

