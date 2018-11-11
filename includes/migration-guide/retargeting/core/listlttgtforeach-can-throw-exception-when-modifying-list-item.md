### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a>List&lt;T&gt;.ForEach, liste öğesi değiştirilirken özel durum oluşturabilir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 sürümünden başlayarak, çağrı koleksiyonundaki bir öğe değiştirilirse bir <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> numaralandırıcısı bir <xref:System.InvalidOperationException?displayProperty=name> özel durumu oluşturur. Daha önceden, bu bir özel durum oluşturmuyordu ancak yarış durumlarına neden olabiliyordu.|
|Öneri|İdeal olarak, bu hiçbir zaman güvenli bir işlem olmadığından kod, liste öğelerini listelerken, listeleri değiştirmeyecek şekilde düzeltilmelidir. Bununla birlikte, bir uygulama önceki davranışa dönmek için .NET Framework 4.0’ı hedefleyebilir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|

