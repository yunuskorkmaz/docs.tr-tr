### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a>Enumerable.Empty&lt;TResult&gt; döndürür örneği her zaman önbelleğe alınmış

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 içinde başlayarak <xref:System.Linq.Enumerable.Empty%60%601> her zaman önbelleğe alınmış bir iç örneğini döndürür <xref:System.Collections.Generic.IEnumerable%601>. Daha önce <xref:System.Linq.Enumerable.Empty%60%601> boş bir önbellek <xref:System.Collections.Generic.IEnumerable%601> API çağrıldı zamanında, bazı durumlarda, yani <xref:System.Linq.Enumerable.Empty%60%601> hızlı ve eşzamanlı olarak, farklı çağrıldı türünün örnekleri farklı çağrılar için döndürülemedi API.|
|Öneri|Önceki davranış belirleyici olduğu için kodu bağımlı olması beklenmez. Ancak, açık boş dizi boş enumerables karşılaştırıldığı ve bazen eşit olması beklenen olası durumda oluşturulmalıdır (<code>new T[0]</code>) kullanmak yerine <xref:System.Linq.Enumerable.Empty%60%601>.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|

