### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Unicode bulunduğunda destek özel göreli URI gösterimi

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Uri> artık özel durum oluşturacak bir <xref:System.NullReferenceException> çağrılırken <xref:System.Uri.TryCreate%2A> Unicode.The basit üretimi içeren belirli göreli URI <xref:System.NullReferenceException> aşağıdadır, eşdeğer iki deyimleri ile:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Yeniden <xref:System.NullReferenceException>, aşağıdakilerin doğru olması gerekir:<ul><li>URI olarak göreli ile eklenerek belirtilmelidir ' http:' ve aşağıdaki kendisiyle ' / /'.</li><li>URI yüzde olarak kodlanmış Unicode veya ayrılmamış simgeler içermelidir.</li></ul>|
|Öneri|Bu davranış bağlı olarak göreli URI'ler izin vermeyecek şekilde kullanıcılar yerine belirtmelidir <xref:System.UriKind.Absolute?displayProperty=nameWithType> bir URI oluştururken.|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|

