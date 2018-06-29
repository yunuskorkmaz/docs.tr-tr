### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>HttpRequest.ContentEncoding özelliği UTF7 engeller

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4. 5 ' başlayarak, UTF-7 kodlama MMC'deki <xref:System.Web.HttpRequest?displayProperty=name>s' gövdesi. Gelen UTF-7 verilerine bağlı olan uygulamalar için verilerin kodları bazı durumlarda düzgün çözülmez.|
|Öneri|İdeal olarak, uygulamalar, kodlama UTF-7 kullanmayacak şekilde güncelleştirilmelidir <xref:System.Web.HttpRequest?displayProperty=name>s. Alternatif olarak, eski davranışı kullanarak geri yüklenebilir <code>aspnet:AllowUtf7RequestContentEncoding</code> özniteliği [appSettings](https://msdn.microsoft.com/library/hh975440(v=vs.110).aspx) öğesi.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|

