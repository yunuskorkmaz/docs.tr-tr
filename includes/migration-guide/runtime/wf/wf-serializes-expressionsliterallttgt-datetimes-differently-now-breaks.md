### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF serileştiren Expressions.Literal&lt;T&gt; tarih/saat farklı artık (özel XAML ayrıştırıcıları keser.)

|   |   |
|---|---|
|Ayrıntılar|İlişkili <xref:System.Windows.Markup.ValueSerializer> nesnesi tarafından dönüştürülür bir <xref:System.DateTime?displayProperty=name> veya <xref:System.DateTimeOffset?displayProperty=name> ikinci nesnesindeki ve <xref:System.DateTime.Millisecond?displayProperty=name> bileşenleri sıfır olmayan ve (için bir <xref:System.DateTime?displayProperty=name> değeri), <xref:System.DateTime.Kind> özellik için özellik öğesi belirtilmeyen değil sözdizimi yerine bir dize. Bu değişiklik verir <xref:System.DateTime?displayProperty=name> ve <xref:System.DateTimeOffset?displayProperty=name> gidiş dönüş değerleri. Nitelik söz dizimindeki giriş XAML'inin doğru çalışmayacağını varsayan özel XAML ayrıştırıcıları.|
|Öneri|Bu değişiklik verir <xref:System.DateTime?displayProperty=name> ve <xref:System.DateTimeOffset?displayProperty=name> gidiş dönüş değerleri. Nitelik söz dizimindeki giriş XAML'inin doğru çalışmayacağını varsayan özel XAML ayrıştırıcıları.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|çalışma zamanı|

