### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Farklı piksel yükseklik öğelerle düz bir liste öğesi kaydırma

|   |   |
|---|---|
|Ayrıntılar|Zaman bir <xref:System.Windows.Controls.ItemsControl?displayProperty=name> sanallaştırma kullanan bir koleksiyon görüntüler (<code>IsVirtualizing=true</code>) ve kaydırma öğesi - (<code>ScrollUnit=Item</code>), ve denetimi, yüksekliğini piksel cinsinden Komşuları farklı bir öğe görüntülemek için kaydırdığında <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> tüm yineleme koleksiyondaki öğe. Kullanıcı arabirimini bu yineleme sırasında yanıt vermiyor; Koleksiyon büyükse, bu yanıt vermemesine algılanan. Diğer durumlarda, daha önceki sürümlerde .NET Framework yineleme gerçekleşir. Örneğin, piksel kaydırma sırasında oluşur (<code>ScrollUnit=Pixel</code>) öğesini kaydırma sırasında bir öğe farklı piksel yüksekliği ile karşılaşıldığında hiyerarşik verileri (gibi bir <xref:System.Windows.Controls.TreeView?displayProperty=name> veya bir <xref:System.Windows.Controls.ItemsControl?displayProperty=name> etkin gruplandırma ile) bir öğesiyle karşılaşıldığında bir alt öğe, komşularına daha farklı sayısı. Öğe kaydırma ve farklı piksel yükseklik servis talebi için yineleme hiyerarşik veri düzenini hataları düzeltmek için .NET Framework 4.6.1 sunulmuştur.  Verileri (hiyerarşi yok) düz ve .NET Framework 4.6.2 Bu durumda, yapmaz ise gerekli değildir.|
|Öneri|Yineleme .NET Framework 4.6.1 ancak önceki sürümlerden - diğer bir deyişle, varsa oluşursa <xref:System.Windows.Controls.ItemsControl?displayProperty=name> iş öğesi-düz bir liste kaydırma farklı piksel height - öğeleriyle iki çözümler vardır:<ol><li>.NET Framework 4.6.2 yükleyin.</li><li>.NET Framework 4.6.1 düzeltmeyi HR 1605 yükleyin.</li></ol>|
|Kapsam|Küçük|
|Sürüm|4.6.1|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|

