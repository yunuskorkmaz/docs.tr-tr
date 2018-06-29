### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Alt öğe (örneğin, ListBox ve DataGrid) ItemsControls olarak kaydırmak zaman zaman oluşturulamıyor özel DataTemplates kullanırken

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda, .NET Framework 4.5 hatada ItemsControls neden oluyor (gibi <xref:System.Windows.Controls.ListBox?displayProperty=name>, <xref:System.Windows.Controls.ComboBox?displayProperty=name>, <xref:System.Windows.Controls.DataGrid?displayProperty=name>, vs.) özel DataTemplates kullanırken, kendi alt öğeye kaydırma değil. Kaydırma (Yedekleme kaydırma sonra) bir kez denenirse, sonra çalışır.|
|Öneri|Bu sorun, .NET Framework 4.5.2 sabit ve bu sürümü (veya sonraki bir sürümünü) .NET Framework'ün yükselterek desteklenebilir. Alternatif olarak, kullanıcılar bu koleksiyonlardaki son öğelerine hala kaydırma çubukları sürükleyin, ancak iki kez bunu başarıyla yapmak denemeniz gerekebilir.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|çalışma zamanı|

