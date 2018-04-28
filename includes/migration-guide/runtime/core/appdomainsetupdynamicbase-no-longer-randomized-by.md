### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup.DynamicBase artık UseRandomizedStringHashAlgorithm tarafından rastgeledir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 değerini önce <xref:System.AppDomainSetup.DynamicBase> UseRandomizedStringHashAlgorithm uygulamanın yapılandırma dosyasında etkinleştirilirse işlemleri veya uygulama etki alanları arasında randomized. .NET Framework 4.6 başlayarak <xref:System.AppDomainSetup.DynamicBase> farklı bir uygulama çalışan örnekleri arasında ve farklı uygulama etki alanları arasında tutarlı bir sonuç döndürür. Dinamik tabanları hala farklı uygulamalar için farklılık gösterir; Bu değişiklik, yalnızca aynı uygulama farklı örnekleri için rastgele adlandırma öğeyi kaldırır.|
|Öneri|Unutmayın, etkinleştirme <code>UseRandomizedStringHashAlgorithm</code> olmayacaktır <xref:System.AppDomainSetup.DynamicBase> rastgele. Rastgele bir taban gerekiyorsa, uygulamanızın kodu yerine bu API aracılığıyla oluşturulması gerekir.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|

