### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>ContentDisposition tarih saatleri biraz farklı bir dize döndürür.

|   |   |
|---|---|
|Ayrıntılar|Dize temsillerini <xref:System.Net.Mime.ContentDisposition?displayProperty=name>ait her zaman saat bileşenini temsil etmek için 4.6 itibaren güncelleştirilen bir <xref:System.DateTime?displayProperty=name> iki basamakla. Uymak için budur [RFC822](http://www.ietf.org/rfc/rfc0822.txt) ve [RFC2822](http://www.ietf.org/rfc/rfc2822.txt). Bu neden <xref:System.Net.Mime.ContentDisposition.ToString> değerlendirme'nın zaman öğelerden birine 10: 00'da önce olduğu senaryolarda 4.6 olarak biraz farklı bir dize döndürecek şekilde. ContentDispositions bazen dizelerine şekilde dönüştürme aracılığıyla seri halde olmadığını unutmayın <xref:System.Net.Mime.ContentDisposition.ToString> işlemleri, seri hale getirme veya GetHashCode çağrıları gözden geçirileceğini.|
|Öneri|Dize temsillerini ContentDispositions farklı .NET Framework sürümlerinden doğru bir başkasına karşılaştıracağız olduğunu beklemiyoruz. Dizelere ContentDispositions, mümkün olduğunda, bir karşılaştırma yapmadan önce dönüştürün.|
|Kapsam|Küçük|
|Sürüm|4.6|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|

