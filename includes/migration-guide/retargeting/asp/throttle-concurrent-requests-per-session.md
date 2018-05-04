### <a name="throttle-concurrent-requests-per-session"></a>Oturum başına eşzamanlı istek kısıtlama

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 daha önce ASP.NET aynı SessionID ile istekleri sıralı olarak yürütür ve ASP.NET her zaman varsayılan olarak tanımlama bilgilerinin aracılığıyla SessionID sorunları. Bir sayfa yanıt uzun sürüyorsa, yalnızca tarayıcıda F5'e basarak da önemli ölçüde sunucu performansını bozar. Kuyruğa alınan istekler izlemek ve belirli bir sınırı aşan istekler sonlandırmak için bir sayaç eklediğimiz düzeltme. Varsayılan değer 50'dir. Sınıra ulaşıldığında, olay günlüğünü ve bir HTTP 500 yanıt IIS günlüğe kaydedilebilir bir uyarı kaydedilir.|
|Öneri|Eski davranışı geri yüklemek için aşağıdaki ayar dışında yeni davranış kabul etmek için web.config dosyasına ekleyebilirsiniz.<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Yeniden hedefleme|

