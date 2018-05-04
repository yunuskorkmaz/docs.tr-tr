### <a name="long-path-support"></a>Uzun yol desteği

|   |   |
|---|---|
|Ayrıntılar|Uygulamalarla hedefleyen (en fazla karakter sayısı 32 K) .NET Framework 4.6.2, uzun yolları desteklenir ve 260 karakter başlangıç (veya <code>MAX_PATH</code>) yolu uzunlukları sınırlama kaldırıldı. .NET Framework 4.6.2 hedeflemek için derlenir uygulamaları için daha önce belirtti yolları kod bir <xref:System.IO.PathTooLongException?displayProperty=name> bir yolu aştığından 260 karakter şimdi throw bir <xref:System.IO.PathTooLongException?displayProperty=name> yalnızca aşağıdaki koşullar altında:<ul><li>Yol uzunluğu değerinden daha büyük <xref:System.Int16.MaxValue> (32.767) karakter.</li><li>İşletim sistemi döndürür <code>COR_E_PATHTOOLONG</code> ya da eşdeğer.</li></ul>.NET Framework 4.6.1 ve önceki sürümlerini hedefleyen uygulamalar için çalışma zamanı otomatik olarak oluşturur bir <xref:System.IO.PathTooLongException?displayProperty=name> her bir yol 260 karakteri aşıyor.|
|Öneri|.NET Framework 4.6.2 hedefleyen uygulamalar için aşağıdakileri ekleyerek arzu değilse, uzun yol desteği dışında seçebilirsiniz <code>&lt;runtime&gt;</code> bölümü, <code>app.config</code> dosyası:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Hedef uygulamalar için .NET Framework'ün önceki sürümlerinde, ancak .NET Framework 4.6.2 çalıştırmak veya daha sonra uzun yol desteklemek için aşağıdakileri ekleyerek kabul <code>&lt;runtime&gt;</code> bölümü, <code>app.config</code> dosyası:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.6.2|
|Tür|Yeniden hedefleme|

