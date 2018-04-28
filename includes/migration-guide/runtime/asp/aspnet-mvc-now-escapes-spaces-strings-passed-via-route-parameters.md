### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC içindeki rota parametreleri aracılığıyla düğümlere geçirilir dizelerde alanları artık çıkışları

|   |   |
|---|---|
|Ayrıntılar|RFC 2396 uygun için rota yollarda boşluk şimdi bir rota Eylem parametrelerinden doldurulurken atlanır. Bu nedenle, ancak <code>/controller/action/some data</code> rota önceden eşleşir <code>/controller/action/{data}</code> ve sağlamak <code>some data</code> veri parametre olarak bunu şimdi sağlayacak <code>some%20data</code> yerine.|
|Öneri|Kod bir rotadaki dizesi parametreleri unescape için güncelleştirilmesi gerekir. Özgün URI gerekirse ile erişilebileceğini <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString API.|
|Kapsam|Küçük|
|Sürüm|4.5.2|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|

