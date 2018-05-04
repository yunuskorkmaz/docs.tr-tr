### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a>WPF TextBox/PasswordBox metin seçimini sistem renkleri izlemiyor

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ve önceki sürümlerde, WPF <code>System.Windows.Controls.TextBox</code> ve <code>System.Windows.Controls.PasswordBox</code> donatıcı katmanı metin seçimde yalnızca getirebilir. Bazı sistem temalar, bu metin, zor okunur yapma occlude.  .NET Framework 4.7.2 ve daha sonra geliştiriciler bu sorunu azaltır donatıcı temelli seçim işleme düzeni etkinleştirme seçeneğiniz vardır.|
|Öneri|Bu değişiklik kullanmak isteyen bir geliştirici, aşağıdaki AppContext bayrağı uygun şekilde ayarlamanız gerekir.  Bu özelliği kullanmak için yüklü olan .NET Framework sürümü 4.7.2 olmalıdır veya daha büyük. Donatıcı tabanlı olmayan seçim etkin için aşağıdaki AppContext bayrağını kullanın.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Yeniden hedefleme|

