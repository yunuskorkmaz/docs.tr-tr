### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>Metin kutusu devre dışı olduğunda WPF seçili TextBox metni farklı bir renk görünür.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 WPF metin kutusu denetiminin devre dışı olduğunda içinde (odak yok), seçili metin kutusunun içindeki denetim etkin olduğunda daha farklı bir renk görünür.|
|Öneri|Önceki (.NET Framework 4.0) davranışı ayarlayarak geri yüklenebilir <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> özelliğine <code>false</code>.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

