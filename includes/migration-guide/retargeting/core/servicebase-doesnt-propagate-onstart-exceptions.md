### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase OnStart özel durumları yayar değil

|   |   |
|---|---|
|Ayrıntılar|Hizmet başlangıç sırasında oluşturulan özel durumlar .NET Framework 4.7 ve önceki sürümlerle çağırana yayılmaz <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.<br/>.NET Framework 4.7.1'i hedefleyen uygulamalar ile başlayarak, çalışma zamanı özel durumları yayar <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> hizmetler başlatılamaz.|
|Öneri|Bir özel durum ise hizmet Başlat, o özel durumu yayılır. Bu, burada başlatmak için hizmetler başarısız durumda tanılanmasına yardımcı olmak. <br/>Bu davranış, istenmeyen ise, dışında aşağıdakileri ekleyerek seçebilirsiniz <AppContextSwitchOverrides> öğesine <runtime> , uygulama yapılandırma dosyasının:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true&quot; /&gt;&#13;&#10;</code></pre>Uygulamanızı 4.7.1 daha önceki bir sürümü hedefliyorsa, ancak bu davranışı olmasını istediğiniz aşağıdakileri ekleyin <AppContextSwitchOverrides> öğesine <runtime> , uygulama yapılandırma dosyasının:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType></li><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType></li></ul>|

