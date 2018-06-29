### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a>WPF DataTemplate öğeleri için UIA görülebilir

|   |   |
|---|---|
|Ayrıntılar|Daha önce <xref:System.Windows.DataTemplate?displayProperty=name> öğeleri için UI Otomasyon görünmez. UI Otomasyonu 4.5 içinde başlayarak, bu öğeler algılar. Bu çok durumda yararlıdır, ancak değil içeren UIA ağaçları bağımlı testleri bölünebilir <xref:System.Windows.DataTemplate?displayProperty=name> öğeleri.|
|Öneri|UI Otomasyonu testleri bu uygulamayı gerekebilir güncelleştirilmiş için UIA ağacı şimdi dahil olmak üzere daha önce görünmez hesap için <xref:System.Windows.DataTemplate?displayProperty=name> öğeleri. Örneğin, diğer yanındaki olması için bazı öğeler beklediğiniz testleri şimdi daha önce görünmez UIA öğeler arasındaki beklediğiniz gerekebilir. Veya yeni değerlerle UIA öğeleri gerekebilir için belirli sayılar veya dizinleri kullanan testleri güncelleştirilemedi.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.DataTemplate.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)?displayProperty=nameWithType></li></ul>|

