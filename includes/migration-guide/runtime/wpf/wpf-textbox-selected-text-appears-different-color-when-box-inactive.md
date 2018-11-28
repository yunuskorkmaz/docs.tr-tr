### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>Metin kutusu etkin olduğunda WPF seçili TextBox metni farklı bir renkte görünür.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 WPF metin kutusu denetimi devre dışı olduğunda, (odağı almasa), kutu içerisinde seçili metin denetimi etkin olduğunda daha farklı bir renkte görünür.|
|Öneri|Ayarlayarak önceki (.NET Framework 4.0) davranış geri yüklenebilir <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> özelliğini <code>false</code>.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

