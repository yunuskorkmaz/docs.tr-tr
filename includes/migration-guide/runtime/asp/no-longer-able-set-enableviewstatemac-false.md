### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Artık mümkün EnableViewStateMac false olarak ayarlamak için

|   |   |
|---|---|
|Ayrıntılar|ASP.NET artık geliştiricilerinin belirtmelerini sağlayan <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> veya <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. Görünüm durumu ileti kimlik doğrulama kodu (MAC), artık ekli görünüm durumu olan tüm istekler için uygulanır. Yalnızca açıkça EnableViewStateMac özellik kümesine uygulamaları <code>false</code> etkilenir.|
|Öneri|EnableViewStateMac kabul, true olarak ve sonuçta elde edilen MAC hataları giderilmesi gerekir (açıklandığı gibi [bu kılavuz](https://support.microsoft.com/kb/2915218), MAC hatalara neden olan özelliklerini bağlı olarak birden çok çözünürlüğü içerir).|
|Kapsam|Ana|
|Sürüm|4.5.2|
|Tür|Çalışma zamanı|

