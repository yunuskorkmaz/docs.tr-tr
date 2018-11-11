### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>WPF TextBox.Text veri bağlama ile zaman uyumsuz olabilir

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda, veri bağlama yazma işlemi sırasında <xref:System.Windows.Controls.TextBox.Text> özelliği değiştirilirse, özellik, veriye bağlı özellik değerinin önceki değerini yansıtır.|
|Öneri|Bunun negatif bir etkisi olmamalıdır. Ancak, <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> özelliğini <code>false</code> olarak ayarlayarak önceki davranışı geri yükleyebilirsiniz.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|

