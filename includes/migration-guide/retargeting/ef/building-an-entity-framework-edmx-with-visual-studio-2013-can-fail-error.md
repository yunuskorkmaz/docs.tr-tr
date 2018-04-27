### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>Visual Studio 2013 ile bir Entity Framework edmx derleme hata ile MSB4062 EntityDeploySplit veya EntityClean görevleri kullanıyorsanız başarısız olabilir

|   |   |
|---|---|
|Ayrıntılar|MSBuild 12.0 Araçları (Visual Studio 2013'te yer alan) geçersiz olduğu eski Entity Framework hedefleri dosyaları neden MSBuild dosya konumları değiştirildi. Sonuç <code>EntityDeploySplit</code> ve <code>EntityClean</code> görevleri başarısız bulamıyor olduklarından <code>Microsoft.Data.Entity.Build.Tasks.dll</code>. Bu sonu araç takımı (MSBuild/VS) değişikliği nedeniyle olmayan bir .NET Framework değişikliği nedeniyle olduğuna dikkat edin. Ancak, geliştirici araçları, yalnızca .NET Framework değil yükseltirken yükseltme sırasında gerçekleşir.|
|Öneri|Entity Framework MSBuild yeni MSBuild düzeni'den itibaren .NET Framework 4.6 ile çalışmak için düzeltilmiştir. Framework'ün bu sürümüne yükseltme, bu sorunu düzeltir. Alternatif olarak, [bu](http://stackoverflow.com/a/24249247/131944) geçici çözüm, hedef dosyaları doğrudan düzeltme eki için kullanılabilir.|
|Kapsam|Ana|
|Sürüm|4.5.1|
|Tür|Yeniden hedefleme|

