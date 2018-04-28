### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue&lt;T&gt;. TryPeek, out parametresi hatalı bir null döndürebilir

|   |   |
|---|---|
|Ayrıntılar|Çok iş parçacıklı bazı senaryolarda <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> true döndürür ancak out parametresi null değeri (yerine doğru Aranan değer) ile doldurur.|
|Öneri|.NET Framework 4.5.1 Bu sorun düzeltilmiştir. Bu çerçeve yükseltme sorunu çözün.|
|Kapsam|Ana|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|

