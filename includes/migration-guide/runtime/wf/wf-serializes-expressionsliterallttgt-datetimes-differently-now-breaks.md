### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF serileştiren Expressions.Literal&lt;T&gt; tarih/saat farklı artık (özel XAML ayrıştırıcıları sonu)

|   |   |
|---|---|
|Ayrıntılar|İlişkili <xref:System.Windows.Markup.ValueSerializer> nesnesi bir <xref:System.DateTime?displayProperty=name> veya <xref:System.DateTimeOffset?displayProperty=name> ikinci nesnesi ve <xref:System.DateTime.Millisecond?displayProperty=name> bileşenleri sıfır olmayan ve (için bir <xref:System.DateTime?displayProperty=name> değer), <xref:System.DateTime.Kind> özelliği için özellik öğesi belirtilmeyen değil bir dize yerine söz dizimi. Bu değişiklik sağlayan <xref:System.DateTime?displayProperty=name> ve <xref:System.DateTimeOffset?displayProperty=name> değerlerinin gidiş dönüşlü olmasına olanak. Nitelik söz dizimindeki giriş XAML'inin doğru çalışmayacağını varsayan özel XAML ayrıştırıcıları.|
|Öneri|Bu değişiklik sağlayan <xref:System.DateTime?displayProperty=name> ve <xref:System.DateTimeOffset?displayProperty=name> değerlerinin gidiş dönüşlü olmasına olanak. Nitelik söz dizimindeki giriş XAML'inin doğru çalışmayacağını varsayan özel XAML ayrıştırıcıları.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|

