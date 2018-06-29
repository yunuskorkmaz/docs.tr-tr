### <a name="systemuri-escaping-now-supports-rfc-3986"></a>System.Uri kaçış artık RFC 3986 destekler

|   |   |
|---|---|
|Ayrıntılar|URI kaçış desteklemek için .NET Framework 4.5 içinde değişti [RFC 3986](http://tools.ietf.org/html/rfc3986). Belirli değişiklikleri şunlardır:<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=name> kaçış karakterleri RFC 3986 dayalı karakter saklıdır.</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=name> ayrılmış karakterleri kaçış değil.</li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> Geçersiz kaçış dizisi karşılaşırsa bir özel durum değil.</li><li>Ayrılmamış kaçış karakterleri, kaçılmamış durumdadır.</li></ul>|
|Öneri|<ul><li>Güncelleştirmenin güvenemeyeceklerini olmayan uygulamalar <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> söz konusu olduğunda geçersiz kaçış dizisi atmak için. Bu tür dizileri doğrudan şimdi algılanabilmesi gerekir.</li><li>Benzer şekilde, Escaped ve Atlanmayan URI ve veri dizeleri .NET Framework 4.0 ve .NET Framework 4.5 değişebilir ve .NET sürümleri arasında doğrudan karşılaştırılmalıdır değil bekler. Bunun yerine, bunlar ayrıştırılması ve tüm karşılaştırmaları yapılmadan önce tek bir .NET sürümünde normalleştirilmiş.</li></ul>|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|

