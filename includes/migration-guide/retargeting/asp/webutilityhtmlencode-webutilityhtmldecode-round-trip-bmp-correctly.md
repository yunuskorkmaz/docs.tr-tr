### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a>WebUtility.HtmlEncode ve WebUtility.HtmlDecode gidiş dönüş BMP doğru

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 için geçirildiğinde, doğru temel çok dilli düzlem (BMP) gidiş dönüş dışında olan karakterler hedefleyen uygulamalar için <xref:System.Net.WebUtility.HtmlDecode(System.String)> yöntemleri.|
|Öneri|Bu değişiklik geçerli uygulamalar üzerinde hiçbir etkisi yoktur, ancak özgün davranışı geri yüklemek için ayarlanmış <code>targetFramework</code> özniteliği <code>&lt;httpRuntime&gt;</code> dışında bir dizeye öğesi &quot;4.5&quot;. Ayrıca <code>unicodeEncodingConformance</code> ve <code>unicodeDecodingConformance</code> özniteliklerini <code>&lt;webUtility&gt;</code> bağımsız olarak hedeflenen .NET Framework'ün bu davranışını denetlemek için yapılandırma öğesi.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li></ul>|

