### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>ListBoxItem IsSelected bağlama ObservableCollection sorun&lt;T&gt;. Taşıma

|   |   |
|---|---|
|Ayrıntılar|Çağırma <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> veya <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> bağlı bir koleksiyonda bir <xref:System.Windows.Controls.ListBox?displayProperty=name> seçili öğeleri gelecekteki seçimi veya unselection, hatalı davranışa neden olabilir <xref:System.Windows.Controls.ListBox?displayProperty=name> öğeleri.|
|Öneri|Çağırma <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> ve <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> yerine <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> bu soruna geçici bir çözüm. Alternatif olarak, bu sorun .NET Framework 4.6 sabit ve .NET Framework'ün bu sürüme yükseltme tarafından desteklenebilir.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

