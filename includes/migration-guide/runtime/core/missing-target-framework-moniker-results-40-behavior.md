### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>Eksik hedef Framework ad 4.0 davranışa neden olur

|   |   |
|---|---|
|Ayrıntılar|Olmadan uygulamalar bir <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> otomatik olarak .NET Framework 4.0 semantiği (quirks) kullanarak derleme düzeyi çalışmaz sırasında uygulanır. Yüksek kaliteli emin olmak için birlikte tüm ikili dosyaları açıkça öznitelikli önerilir bir <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> bunlar yerleşik ile .NET Framework sürümünü gösteren. Proje dosyasında bir hedef framework ad kullanarak otomatik olarak uygulamak MSBuild neden Not bir <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name>.|
|Öneri|A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> doğrudan derleme veya bir hedef framework belirterek öznitelik ekleme yoluyla sağlanmalı [proje dosyası veya özellikler GUI Visual Studio'nun proje](http://blogs.msdn.com/b/visualstudio/archive/2010/05/19/visual-studio- managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework.aspx).|
|Kapsam|Ana|
|Sürüm|4,5|
|Tür|çalışma zamanı|

