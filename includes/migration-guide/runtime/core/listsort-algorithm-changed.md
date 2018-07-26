### <a name="listsort-algorithm-changed"></a>List.Sort algoritma değişti

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 içinde başlayan <xref:System.Collections.Generic.List%601?displayProperty=name>'s Sıralama algoritması (Hızlı sıralama yerine aşağıdaki bir sıralama olacak şekilde) olarak değişti. <xref:System.Collections.Generic.List%601?displayProperty=name>ın sıralama kararlı olamazdı, ancak bu değişiklik, kararsız yollarla sıralamak farklı senaryolar neden olabilir. Bu, yalnızca eşdeğer öğeleri sonraki çağrılar API'sinin farklı sırada sıralama yapılabilir anlamına gelir.|
|Öneri|Çünkü eski Sıralama algoritması da (biraz farklı şekillerde rağmen) kararsız, eşdeğer öğeleri her zaman belirli bir sıraya göre sıralama bağımlı kod olmalıdır. Üzerinde bağlı ve eski davranışı ile lucky kod örneklerini varsa, bu kod öğeleri istenen sırada belirleyici sıralayacağını bir karşılaştırıcı kullanmak için güncelleştirilmesi gerekir.|
|Kapsam|Geçirgen|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|

