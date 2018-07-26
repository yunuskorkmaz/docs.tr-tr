### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a>Liste&lt;T&gt;. ForEach liste öğesi değiştirirken özel durumu oluşturabilecek

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 içinde başlayan bir <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> Numaralandırıcı oluşturur bir <xref:System.InvalidOperationException?displayProperty=name> arama koleksiyondaki bir öğe değiştirilirse özel durum. Daha önce bir özel durum oluşturması beklenmiyor ancak yarış koşulları neden olabilir.|
|Öneri|İdeal olarak, liste öğelerini, hiçbir zaman güvenli bir işlemi olduğundan numaralandırılırken değiştirmek için kod düzeltilmelidir. Önceki davranışa dönmek yine de bir uygulamayı .NET Framework 4.0 hedefleyebilir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|

