### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>Bir WPF TreeView veya gruplandırılmış liste kutusunda bir VirtualizingStackPanel kaydırma bir yanıt vermemesine neden olabilir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework v4.5 içinde bir WPF kaydırma <xref:System.Windows.Controls.TreeView?displayProperty=name> görünüm penceresinin içinde kenar boşlukları varsa sanallaştırılmış yığında paneli askıda neden olabilir (öğeler arasında <xref:System.Windows.Controls.TreeView?displayProperty=name>, örneğin veya bir ItemsPresenter öğede). Kenar boşlukları olsa bile ek olarak, bazı durumlarda, görünümdeki farklı boyutlarda öğeleri tutarsızlığa neden olabilir.|
|Öneri|Bu hata, .NET Framework 4.5.1 yükselterek önlenebilir. Alternatif olarak, kenar boşlukları görünüm koleksiyonlarından kaldırılabilir (gibi <xref:System.Windows.Controls.TreeView?displayProperty=name>s) sanallaştırılmış yığın içindeki tüm öğeler içeriyorsa paneller aynı boyuttadır.|
|Kapsam|Ana|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|

