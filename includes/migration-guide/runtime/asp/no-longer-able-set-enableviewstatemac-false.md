### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Artık şunları EnableViewStateMac false olarak ayarlayın.

|   |   |
|---|---|
|Ayrıntılar|ASP.NET belirlemek geliştiriciler artık sağlayan <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> veya <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. Görünüm durumu ileti kimlik doğrulama kodu (MAC), artık katıştırılmış görünüm durumuna sahip tüm istekler için zorlanır. Yalnızca açıkça EnableViewStateMac özellik kümesine uygulamaların <code>false</code> etkilenir.|
|Öneri|EnableViewStateMac varsayıldı, doğru olmasını ve ortaya çıkan MAC hataları çözümlenemedi. (açıklandığı şekilde [bu kılavuz](https://support.microsoft.com/kb/2915218), MAC hataları neden olan özelliklerini bağlı olarak birden çok çözümler içerir).|
|Kapsam|Ana|
|Sürüm|4.5.2|
|Tür|Çalışma zamanı|

