### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>UTF7 HttpRequest.ContentEncoding özelliği engeller

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4. 5 ' başlayarak, UTF-7 kodlaması MMC'deki <xref:System.Web.HttpRequest?displayProperty=name>s' gövdesi. Gelen UTF-7 verilerine bağlı olan uygulamalar için verilerin kodları bazı durumlarda düzgün çözülmez.|
|Öneri|İdeal olarak, uygulamalar UTF-7 içinde kodlama kullanmayacak şekilde güncelleştirilmelidir <xref:System.Web.HttpRequest?displayProperty=name>s. Alternatif olarak, eski davranışı kullanılarak geri yüklenebilir <code>aspnet:AllowUtf7RequestContentEncoding</code> özniteliği [appSettings](https://msdn.microsoft.com/library/hh975440(v=vs.110).aspx) öğesi.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|

