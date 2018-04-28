### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Icon.ToBitmap, PNG çerçeveler simgelerle başarıyla Bitmap nesnelerine dönüştürür.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 hedefleyen uygulamalar ile başlayan <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yöntemi başarıyla PNG çerçeveler simgelerle Bitmap nesnelerine dönüştürür. .NET Framework 4.5.2 ve önceki sürümlerini hedefleyen uygulamalarda <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yöntemi atar bir <xref:System.ArgumentOutOfRangeException> PNG çerçeveler simgesi nesne varsa, özel durum. Bu değişiklik, .NET Framework 4.6 hedeflemek için derlenir ve özel işleme için uygulamanıza uygulamaları etkiler <xref:System.ArgumentOutOfRangeException> simgesi nesne PNG çerçeveler olduğunda oluşur. .NET Framework 4.6 altında çalışırken, dönüştürme başarılı bir <xref:System.ArgumentOutOfRangeException> Hayır artık oluşturulur ve bu nedenle özel durum işleyici artık çağrılır.|
|Öneri|Bu davranış istenmeyen ise, aşağıdaki öğeyi ekleyerek önceki davranış tutabilirsiniz <code>&lt;runtime&gt;</code> app.config dosyasının:<pre><code class="language-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>App.config dosyasını zaten varsa <code>AppContextSwitchOverrides</code> öğesi, bu gibi değer özniteliğine sahip yeni bir değer birleştirilmiş:<pre><code class="language-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.6|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|

