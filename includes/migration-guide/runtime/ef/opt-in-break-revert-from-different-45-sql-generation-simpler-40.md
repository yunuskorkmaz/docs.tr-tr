### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Öğesinden farklı 4.5 SQL üretimi için daha basit 4.0 SQL üretimi dönmek için katılımı sonu

|   |   |
|---|---|
|Ayrıntılar|BİRLEŞİM deyimleri üretip ve bir çağrı içeren sorgular ilk olmadan sınırlama işlemi için OrderBy şimdi kullanarak üretmek daha basit SQL. .NET Framework 4.5 sürümüne yükselttikten sonra bu sorguları önceki sürümlerinden daha karmaşık SQL üretti.|
|Öneri|Bu özellik varsayılan olarak devre dışıdır. Entity Framework performans düşüşüne neden ek JOIN deyimleri oluşturursa, aşağıdaki girişini ekleyerek bu özelliği etkinleştirebilirsiniz <code>&lt;appSettings&gt;</code> uygulama yapılandırma (app.config) dosyasının:<pre><code class="language-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Geçirgen|
|Sürüm|4.5.2|
|Tür|Çalışma zamanı|

