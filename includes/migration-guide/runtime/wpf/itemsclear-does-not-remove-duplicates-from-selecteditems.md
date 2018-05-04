### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear çoğaltmaları SelectedItems kaldırmaz

|   |   |
|---|---|
|Ayrıntılar|Çoğaltmaları (ile Çoklu seçim etkin) bir seçici sahip olduğunu varsayın kendi <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> aynı öğe koleksiyonu - görünür birden çok kez.  Bu öğeleri (örneğin Items.Clear çağırarak) veri kaynağı'ndan kaldırma başarısız bunları kaldırmak <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>; yalnızca ilk örneği kaldırılır. Ayrıca, sonraki kullanımını <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (örneğin SelectedItems.Clear()) gibi sorunlarla <xref:System.ArgumentException?displayProperty=name>, çünkü <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> artık veri kaynağında olmayan öğeler içeriyor.|
|Öneri|Mümkünse, .NET Framework 4.6.2 yükseltin.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|

