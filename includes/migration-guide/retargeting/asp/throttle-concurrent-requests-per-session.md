### <a name="throttle-concurrent-requests-per-session"></a>Oturum başına eşzamanlı istek kısıtlama

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 daha önce ASP.NET ile aynı SessionID istekleri sıralı olarak yürütür ve ASP.NET varsayılan olarak her zaman tanımlama bilgileri ile oturum kimliği verir. Bir sayfa yanıt uzun sürerse, yalnızca tarayıcıda F5'e basarak, önemli ölçüde sunucu performansını bozar. Düzeltme kuyruğa alınan istekler izlemek ve bunlar belirli bir sınırı aşan istekleri sonlandırmak için bir sayaç ekledik. Varsayılan değer 50'dir. Sınıra ulaşıldığında, olay günlüğünü ve bir HTTP 500 yanıt IIS günlüğe kaydedilebilir bir uyarı günlüğe kaydedilir.|
|Öneri|Eski davranışı geri yüklemek için aşağıdaki ayarı dışında yeni davranış geri çevirmek için web.config dosyasına ekleyebilirsiniz.<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Yeniden hedefleme|

