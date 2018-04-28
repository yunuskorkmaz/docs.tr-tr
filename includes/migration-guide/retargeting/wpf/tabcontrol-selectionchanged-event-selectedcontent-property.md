### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a>TabControl SelectionChanged olayı ve SelectedContent özelliği

|   |   |
|---|---|
|Ayrıntılar|4.7.1, .NET Framework ile başlayan bir <xref:System.Windows.Controls.TabControl> değerini güncelleştirmeleri kendi <xref:System.Windows.Controls.TabControl.SelectedContent> oluşturma işlemi önce özellik <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> kendi seçim değiştiğinde olay. .NET Framework 4.7 ve önceki sürümlerinde SelectedContent güncelleştirmeye olayından sonra oldu.|
|Öneri|.NET Framework 4.7.1 hedefleyen veya daha sonra bu dışında seçebilirsiniz uygulamalar değiştirin ve aşağıdaki ekleyerek eski davranışı kullanmak <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyasının:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Daha sonra yeni davranışı aşağıdaki satırı ekleyerek etkinleştirebilirsiniz veya .NET Framework 4.7.1 çalıştırıyorsanız .NET Framework 4.7 veya önceki ancak hedef uygulamaları <code>&lt;runtime&gt;</code> uygulama .configuration dosyasının:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|

