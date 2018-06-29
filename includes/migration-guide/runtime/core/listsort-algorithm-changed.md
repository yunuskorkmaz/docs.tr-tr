### <a name="listsort-algorithm-changed"></a>List.Sort algoritma değişti

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 içinde başlayarak <xref:System.Collections.Generic.List%601?displayProperty=name>'s Sıralama algoritması (Hızlı sıralama yerine introspective bir sıralama olacak şekilde) değişti. <xref:System.Collections.Generic.List%601?displayProperty=name>kişinin sıralama hiçbir zaman kararlı açıldı, ancak bu değişiklik kararsız şekilde sıralamak farklı senaryolar neden olabilir. Yalnızca API sonraki çağrılar farklı sıralardaki eşdeğer öğeleri sıralama yapılabilir anlamına gelir.|
|Öneri|Çünkü eski Sıralama algoritması da (biraz farklı şekillerde rağmen) kararsız, her zaman belirli bir sırada sıralama eşdeğer öğeleri bağımlı kod olmalıdır. Bağlı olarak ve eski davranışa şanslı kod örneklerini varsa, bu kodu istenen sırada öğeleri belirleyici biçimde sıralayacağını bir karşılaştırıcı kullanacak şekilde güncelleştirilmesi gerekir.|
|Kapsam|Geçirgen|
|Sürüm|4,5|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|

