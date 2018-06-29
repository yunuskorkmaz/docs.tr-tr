### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>ContentDisposition tarih/saat biraz farklı bir dize döndürür.

|   |   |
|---|---|
|Ayrıntılar|Dize gösterimlerini <xref:System.Net.Mime.ContentDisposition?displayProperty=name>ait her zaman saat bileşenini temsil etmek için 4.6 başlayan güncelleştirilen bir <xref:System.DateTime?displayProperty=name> iki basamaklı. Uymak üzere budur [RFC822](http://www.ietf.org/rfc/rfc0822.txt) ve [RFC2822](http://www.ietf.org/rfc/rfc2822.txt). Bu neden <xref:System.Net.Mime.ContentDisposition.ToString> değerlendirme 's zaman noktalarından 10: 00'da önce bulunduğu biraz farklı bir dize senaryolarda 4.6 döndürmek için. Dizeler için bu nedenle hiçbir dönüştürme aracılığıyla ContentDispositions bazen serileştirilir Not <xref:System.Net.Mime.ContentDisposition.ToString> işlemleri, seri hale getirme veya GetHashCode aramalar gözden geçirileceğini.|
|Öneri|ContentDispositions dize gösterimlerini farklı .NET Framework sürümlerinden düzgün bir şekilde karşılaştırır, beklemediğiniz. Dizeleri ContentDispositions, mümkünse, bir karşılaştırma yapmadan önce dönüştürün.|
|Kapsam|Küçük|
|Sürüm|4.6|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|

