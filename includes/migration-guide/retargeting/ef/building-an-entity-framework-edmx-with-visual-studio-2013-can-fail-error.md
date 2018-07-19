### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>Visual Studio 2013 ile bir Entity Framework edmx derleme hata ile MSB4062 EntityDeploySplit veya EntityClean görevleri kullanıyorsanız başarısız olabilir

|   |   |
|---|---|
|Ayrıntılar|MSBuild 12.0 Araçları (Visual Studio 2013'te dahil), MSBuild dosya konumları, neden geçersiz olduğu eski Entity Framework MSBuild değiştirildi. Sonuç <code>EntityDeploySplit</code> ve <code>EntityClean</code> görevler başarısız bulamadı çünkü <code>Microsoft.Data.Entity.Build.Tasks.dll</code>. Bu kesme araç takımı (MSBuild/VS) değişiklik nedeniyle, olmayan bir .NET Framework değişikliği nedeniyle olduğunu unutmayın. Ancak, yalnızca .NET Framework yükseltmiyorsanız, geliştirici araçları, yükseltme sırasında gerçekleşir.|
|Öneri|Entity Framework MSBuild, .NET Framework 4.6 yeni MSBuild Düzen başlangıçta çalışmak için sabittir. Framework'ün bu sürümüne yükseltme, bu sorunu çözecektir. Alternatif olarak, [bu](http://stackoverflow.com/a/24249247/131944) geçici çözüm, MSBuild doğrudan düzeltme eki için kullanılabilir.|
|Kapsam|Büyük|
|Sürüm|4.5.1|
|Tür|Yeniden hedefleme|

