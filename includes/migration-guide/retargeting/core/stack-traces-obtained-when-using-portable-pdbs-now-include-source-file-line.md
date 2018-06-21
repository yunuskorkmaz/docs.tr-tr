### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a>Taşınabilir pdb şimdi kullanırken elde Yığın izlemeleri istediyseniz kaynak dosya ve çizgi bilgilerini içerir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ile başlayarak, taşınabilir pdb kullanırken elde Yığın izlemeleri istendiğinde kaynak dosya ve çizgi bilgilerini içerir. .NET Framework 4.7.2, kaynak dosya ve satır'den önceki sürümlerde bilgi taşınabilir pdb açıkça istenmiş olsa bile kullanırken kullanılamaz durumda olurdu.|
|Öneri|.NET Framework 4.7.2 hedefleyen uygulamalar için kaynak dosya ve çizgi bilgilerini aşağıdakileri ekleyerek arzu değilse, taşınabilir pdb kullanırken seçebilirsiniz <code>&lt;runtime&gt;</code> bölümü, <code>app.config</code> dosyası:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Hedefleyen uygulamalar için .NET Framework'ün önceki sürümlerinde, ancak .NET Framework 4.7.2 çalıştırmak veya daha sonra kaynak dosya ve çizgi bilgilerini taşınabilir pdb aşağıdakileri ekleyerek kullanırken kabul <code>&lt;runtime&gt;</code> , bölümünü<code>app.config</code>dosyası:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)?displayProperty=nameWithType><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)?displayProperty=nameWithType></li></ul>|

