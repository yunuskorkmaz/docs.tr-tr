### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>Kendi işleyicisi bir Windows Forms ileti kutusu görüntüleniyorsa PreviewLostKeyboardFocus sürekli olarak adlandırılır

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5, çağırma başlayarak <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> gelen bir <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> işleyici ileti kutusu kapatıldığında, büyük olasılıkla ileti kutularının sonsuz bir döngüde kaynaklanan yeniden tetiklenecek işleyici neden olur.|
|Öneri|Bu sorunu çözmek için iki seçenek vardır:<ol><li>Çağırarak kalmayabilir <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> yerine <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</li><li>İleti kutusu göstererek kalmayabilir bir <xref:System.Windows.UIElement.LostKeyboardFocus?displayProperty=nameWithType> olay işleyicisi (tersine bir <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=name> olay işleyicisi).</li></ol>|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|

