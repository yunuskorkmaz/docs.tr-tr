### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>ArgumentOutOfRangeException DataGridCellsPanel.BringIndexIntoView oluşturur

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> zaman uyumsuz olarak sütun sanallaştırma etkinleştirildi, ancak sütun genişliklerini henüz karar verilmemiştir olduğunda çalışır.  Zaman uyumsuz iş gerçekleşmeden önce sütunları kaldırdıysanız bir <xref:System.ArgumentOutOfRangeException?displayProperty=name> oluşabilir.|
|Öneri|Aşağıdakilerden herhangi biri:<ol><li>.NET 4.7'ye yükseltin.</li><li>Son bakım düzeltme eki için .NET 4.6.2 yükleyin.</li><li>Zaman uyumsuz yanıtı kadar sütunları kaldırma kaçının <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> tamamlandı.</li></ol>|
|Kapsam|Kenar|
|Sürüm|4.6.2|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|

