### <a name="systemuri-parsing-adheres-to-rfc-3987"></a>RFC 3987 aynılarını System.Uri ayrıştırma

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 birkaç bakımdan URI ayrıştırma değiştirdi. Ancak, bu değişiklikler yalnızca .NET Framework 4.5 hedefleme kod etkileyeceğini unutmayın. İkili hedefleri, .NET Framework 4.0 eski davranışı izlenir. .NET Framework 4.5 URI ayrıştırma değişiklikleri içerir:<ul><li>Ayrıştırma URI normalleştirme ve karakter RFC 3987 son IRI kurallarında göre denetimi gerçekleştirir.</li><li>Unicode normalleştirme form C yalnızca URI'ın ana bilgisayar kısmı üzerinde gerçekleştirilir.</li><li>Geçersiz mailto: URI'ler bir özel durum neden olur.</li><li>Sondaki nokta yol kesimi sonunda şimdi korunur.</li><li><code>file://</code> URI değil kaçış <code>?</code> karakter.</li><li>Unicode denetim karakterleri <code>U+0080</code> aracılığıyla <code>U+009F</code> desteklenmez.</li><li>Virgül karakteri <code>,</code> veya <code>%2c</code> otomatik olarak atlanmayan değildir.</li></ul>|
|Öneri|Eski .NET Framework 4.0 URI ayrıştırma semantiğini (bunlar genellikle değil) gerekliyse, .NET Framework 4.0 hedefleme tarafından kullanılabilir. Bu kullanılarak gerçekleştirilebilir bir <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> derleme üzerinde ya da 'Proje Özellikleri' sayfasında Visual Studio'nun proje sistem kullanıcı Arabirimi aracılığıyla.|
|Kapsam|Ana|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Uri.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.String,System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.String,System.UriKind)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.Uri,System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li></ul>|

