### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>İş akışı sağlaması için SHA1 MD5 ' değiştirildi

|   |   |
|---|---|
|Ayrıntılar|Visual Studio ile hata ayıklama desteklemek için bir karma algoritması kullanan bir iş akışı örneği için bir sağlama iş akışı çalışma zamanı oluşturur. .NET Framework 4.6.2 ve önceki sürümleri, iş akışı sağlama toplamı karma FIPS BIOS'taki sorunları nedeniyle MD5 algoritması kullanılır. .NET Framework 4.7 ile başlayarak, algoritma SHA1'dir. Kodunuzu bu sağlama kalıcı, uyumsuz olacaktır.|
|Öneri|Kodunuzu bir sağlama toplamı hatası nedeniyle iş akışı örnekleri yükleyemiyor ise, ayarı deneyin <code>AppContext</code> geçiş &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; true. Kod:<pre><code class="language-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>Veya yapılandırma:<pre><code class="language-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7|
|Tür|Yeniden hedefleme|

