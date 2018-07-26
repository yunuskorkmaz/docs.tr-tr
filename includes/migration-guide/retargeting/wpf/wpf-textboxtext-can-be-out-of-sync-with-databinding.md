### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>WPF TextBox.Text eşitleme dışı olabilir bağlamada

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda, <xref:System.Windows.Controls.TextBox.Text> veri bağlama yazma işlemi sırasında özellik değiştirilirse özelliği databound özellik değerinin önceki değerini yansıtır.|
|Öneri|Bunun negatif bir etkisi olmamalıdır. Ancak, ayarlayarak önceki davranış geri yükleyebilirsiniz <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> özelliğini <code>false</code>.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|

