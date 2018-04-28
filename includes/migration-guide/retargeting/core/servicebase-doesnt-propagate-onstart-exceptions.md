### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase OnStart özel durumlar yayılması değil

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7 ve önceki sürümlerinde hizmeti başlatma sırasında oluşturulan özel durumları çağırana yayılmaz <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>. .NET Framework 4.7.1 hedefleyen uygulamalar ile başlayarak, çalışma zamanı özel durumları yayar <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> başlatılamaz Hizmetleri için.|
|Öneri|Bir özel durum ise Hizmeti Başlat, bu özel durum yayılır. Bu, burada başlatmak için hizmetler başarısız durumda tanılamanıza yardımcı olmalıdır. Bu davranış istenmeyen ise, onu dışında aşağıdakileri ekleyerek seçebilirsiniz <AppContextSwitchOverrides> öğesine <runtime> uygulama yapılandırma dosyasının:<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true&quot; /&gt;&#13;&#10;</code></pre>4.7.1 daha önceki bir sürümü, uygulamanızın hedefler ancak bu davranış olmasını istiyorsanız aşağıdakileri ekleyin <AppContextSwitchOverrides> öğesine <runtime> uygulama yapılandırma dosyasının:<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType></li><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType></li></ul>|

