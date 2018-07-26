### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>TextBlock denetimi üst IsEnabled özelliğinin değiştirilmesi tüm alt denetimler etkiler

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2, değiştirme ile başlayarak <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> üst öğesinin özellik bir <xref:System.Windows.Controls.TextBlock?displayProperty=name> denetimi etkiler (örneğin, köprüler ve düğmeler) tüm alt denetimler <xref:System.Windows.Controls.TextBlock?displayProperty=name> denetimi. İçinde .NET Framework 4.6.1 ve önceki sürümlerle denetleyen bir <xref:System.Windows.Controls.TextBlock?displayProperty=name> her zaman durumunu yansıtmıyor <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> özelliği <xref:System.Windows.Controls.TextBlock?displayProperty=name> üst.|
|Öneri|Yok. Bu değişiklik içindeki denetimlerin yönelik beklenen davranışın uyan bir <xref:System.Windows.Controls.TextBlock?displayProperty=name> denetimi.|
|Kapsam|Küçük|
|Sürüm|4.6.2|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|

