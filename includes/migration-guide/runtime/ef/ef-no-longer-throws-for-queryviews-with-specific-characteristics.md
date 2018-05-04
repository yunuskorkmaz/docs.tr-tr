### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF QueryViews için belirli özelliklere sahip artık oluşturur.

|   |   |
|---|---|
|Ayrıntılar|Entity Framework artık oluşturur bir <xref:System.StackOverflowException?displayProperty=name> bir uygulama bir 0.. 1 çokluğa sahip bir QueryView içeren bir sorgu yürüttüğünde özel durum ilgili varlıkları sorgu bir parçası olarak dahil girişiminde gezinti özelliği. Örneğin, çağıran tarafından <code>.Include(e =&gt; e.RelatedNavProp)</code>.|
|Öneri|Bu değişiklik, yalnızca 1 ile QueryViews kullanan kodu etkiler-0.. 1 çokluğa çalışan bu çağrı sorguladığında ilişkiler. İçerir. Güvenilirliğini artırır ve neredeyse tüm uygulamalar için saydam olmalıdır. Beklenmeyen davranışlara neden olur, ancak bunu aşağıdaki girişini ekleyerek devre dışı bırakabilirsiniz <code>&lt;appSettings&gt;</code> uygulamanın yapılandırma dosyasının:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.5.2|
|Tür|Çalışma zamanı|

