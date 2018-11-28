### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a>Enumerable.Empty&lt;TResult&gt; döndürür örnek her zaman önbelleğe alınmış

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 içinde başlayan <xref:System.Linq.Enumerable.Empty%60%601> her zaman önbelleğe alınmış bir dahili örnek döndüren <xref:System.Collections.Generic.IEnumerable%601>. Daha önce <xref:System.Linq.Enumerable.Empty%60%601> boş bir önbellek <xref:System.Collections.Generic.IEnumerable%601> API çağrıldı zaman, bazı koşullarda, yani <xref:System.Linq.Enumerable.Empty%60%601> hızlı bir şekilde ve aynı anda farklı çağrıldı türün örneklerinin farklı çağrılar için döndürülemedi API.|
|Öneri|Önceki davranışı belirleyici olduğu için kodu bağımlı beklenmez. Ancak, boş enumerables karşılaştırıldığı ve bazen eşit olması beklenen olası durumda açık boş diziler oluşturulmalıdır (<code>new T[0]</code>) kullanmak yerine <xref:System.Linq.Enumerable.Empty%60%601>.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|

