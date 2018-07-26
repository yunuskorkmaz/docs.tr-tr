### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>Bir WPF TreeView veya bir VirtualizingStackPanel gruplandırılmış liste kutusunda kaydırma bir yanıt vermemesine neden olabilir

|   |   |
|---|---|
|Ayrıntılar|Bir WPF .NET Framework v4.5, kaydırma <xref:System.Windows.Controls.TreeView?displayProperty=name> görünüm penceresinin içinde kenar boşlukları varsa sanallaştırılmış bir yığın paneli askıda neden olabilir (bulunan öğeler arasındaki <xref:System.Windows.Controls.TreeView?displayProperty=name>, örneğin veya ItemsPresenter öğe). Kenar boşlukları olsa bile ek olarak, bazı durumlarda, farklı boyutta öğeleri görünümünde tutarsızlığa neden olabilir.|
|Öneri|Bu hata, .NET Framework 4.5.1 yükselterek önlenebilir. Alternatif olarak, kenar boşlukları görünümü koleksiyonlardan kaldırılabilir (gibi <xref:System.Windows.Controls.TreeView?displayProperty=name>s) sanallaştırılmış yığın içindeki tüm öğeleri içeriyorsa panelleri aynı boyuttadır.|
|Kapsam|Büyük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|

