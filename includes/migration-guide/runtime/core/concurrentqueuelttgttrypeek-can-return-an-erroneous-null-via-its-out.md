### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue&lt;T&gt;. TryPeek, out parametresinin hatalı bir null döndürebilir

|   |   |
|---|---|
|Ayrıntılar|Çok iş parçacıklı bazı senaryolarda <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> true döndürür ancak out parametresi (doğru baktı değeri) yerine null bir değerle doldurun.|
|Öneri|.NET Framework 4.5.1 Bu sorun düzeltilmiştir. Bu çerçeve için yükseltme sorunu çözün.|
|Kapsam|Büyük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|

