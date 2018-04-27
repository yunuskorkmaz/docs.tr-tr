### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>WPF ListBox, ListView veya seçili öğeleri içeren DataGrid arama Items.Refresh öğesinde görünmesi yinelenen öğeleri neden olabilir

|   |   |
|---|---|
|Ayrıntılar|İçinde seçili öğeleri sırada ListBox.Items.Refresh içinden kodu çağırma .NET Framework 4.5 içinde bir <xref:System.Windows.Controls.ListBox?displayProperty=name> seçilen öğeler listesinde çoğaltılacak neden olabilir. İle benzer bir sorun oluşur <xref:System.Windows.Controls.ListView?displayProperty=name> ve <xref:System.Windows.Controls.DataGrid?displayProperty=name>. Bu .NET Framework 4.6 düzeltilmiştir.|
|Öneri|Bu sorunu çözmek programlı şekilde öğelerden önce unselecting tarafından çalışılan <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> olarak adlandırılır ve aramayı tamamladıktan sonra daha sonra yeniden seçme. Alternatif olarak, bu sorun .NET Framework 4.6 sabit ve .NET Framework'ün bu sürüme yükseltme tarafından desteklenebilir.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|

