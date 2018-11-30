### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC artık alanları dizelerinde de rota parametreleri aracılığıyla düğümlere geçirilir çıkışları

|   |   |
|---|---|
|Ayrıntılar|RFC 2396 uymak için rota yollarda alanları artık bir rota eylemi parametrelerinden doldurulurken atlanır. Bu nedenle, oysa <code>/controller/action/some data</code> rota daha önce eşleşir <code>/controller/action/{data}</code> ve sağlayın <code>some data</code> veri parametre olarak, artık sağlayacak <code>some%20data</code> bunun yerine.|
|Öneri|Kod bir rotadaki dizesi parametreleri unescape güncelleştirilmesi gerekir. Özgün bir URI gerekirse ile erişilebileceğini <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString API.|
|Kapsam|İkincil|
|Sürüm|4.5.2|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|

