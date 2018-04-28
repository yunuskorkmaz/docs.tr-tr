### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>Tüm alt denetimleri etkiler TextBlock denetim üst IsEnabled özelliğini değiştirme

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2, değiştirme başlangıç <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> üst öğesinin özelliği bir <xref:System.Windows.Controls.TextBlock?displayProperty=name> denetim etkiler (örneğin, bağlar ve düğmeleri) tüm alt denetimleri <xref:System.Windows.Controls.TextBlock?displayProperty=name> denetim. .NET Framework 4.6.1 ve önceki sürümlerinde içinde denetimleri bir <xref:System.Windows.Controls.TextBlock?displayProperty=name> her zaman durumunu yansıtacak değil <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> özelliği <xref:System.Windows.Controls.TextBlock?displayProperty=name> üst.|
|Öneri|Yok. Bu değişiklik içinde denetimleri için beklenen bir davranış uyan bir <xref:System.Windows.Controls.TextBlock?displayProperty=name> denetim.|
|Kapsam|Küçük|
|Sürüm|4.6.2|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|

