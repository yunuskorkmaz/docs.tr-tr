### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>DataObject.GetData, verileri artık UTF-8 olarak alır.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4 hedef ya da .NET Framework 4.5.1 veya önceki sürümleri çalıştıran uygulamalar için <code>DataObject.GetData</code> HTML biçimli verileri bir ASCII dize olarak alır. Sonuç olarak, ASCII olmayan karakterler (karakter, ASCII kodları 0x7F büyük) iki rastgele karakterler temsil edilir.<p/>Uygulamalar için .NET Framework 4.5 veya üstü ve .NET Framework 4.5.2, çalıştırılacak hedef <code>DataObject.GetData</code> UTF-0x7F büyük karakterler doğru şekilde temsil eden 8 HTML biçimli verileri alır.|
|Öneri|HTML biçimli dize kodlama sorun için geçici çözüm uygulanan varsa (örneğin, açıkça kodlama HTML dizesi tarafından alınan panodan geçirerek <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=name>) ve sürüm 4 için 4.5 uygulamanızdan yeniden hedefleme, geçici çözüm kaldırılması gerekir. Eski davranışı herhangi bir nedenden dolayı gerekirse, uygulama bu davranışı sağlamak için .NET Framework 4.0 hedefleyebilirsiniz.|
|Kapsam|Kenar|
|Sürüm|4.5.2|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|

