### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>WPF TextBox.Text eşitleme Veri bağlamada

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda, <xref:System.Windows.Controls.TextBox.Text> özellik özelliği databinding yazma işlemi sırasında değiştirilirse veriye bağlı özellik değeri önceki değerini gösterir.|
|Öneri|Bunun negatif bir etkisi olmamalıdır. Ancak, önceki davranış ayarlayarak geri yükleyebilirsiniz <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> özelliğine <code>false</code>.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|

