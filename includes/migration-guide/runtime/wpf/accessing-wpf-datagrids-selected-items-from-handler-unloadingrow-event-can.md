### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>Bir WPF DataGrid'in seçili öğeler bir DataGrid'in UnloadingRow olay işleyicisinden erişme NullReferenceException neden olabilir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5, olay işleyicileri için bir hata nedeniyle <xref:System.Windows.Controls.DataGrid> kapsayan bir satır kaldırılmasını olayların neden olabilecek bir <xref:System.NullReferenceException?displayProperty=name> eriştiklerinde durum için <xref:System.Windows.Controls.DataGrid>ait <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> veya <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> özellikleri.|
|Öneri|Bu sorun, .NET Framework 4. 6 ' sabit ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|

