### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>Visual Studio 2013 ile bir Entity Framework edmx oluşturma işlemi, EntityDeploySplit veya EntityClean görevleri kullanılıyorsa MSB4062 hatasıyla başarısız olabilir

|   |   |
|---|---|
|Ayrıntılar|MSBuild 12.0 araçlarındaki (Visual Studio 2013’e dahildir) MSBuild dosya konumları değiştirilmiş ve eski Entity Framework hedef dosyalarının geçersiz olmasına neden olmuştur. Sonuç olarak, <code>EntityDeploySplit</code> ve <code>EntityClean</code> görevleri <code>Microsoft.Data.Entity.Build.Tasks.dll</code> dosyasını bulamadıkları için başarısız olur. Bu kesintinin bir .NET Framework değişikliğinden değil bir araç takımı (MSBuild/VS) değişikliğinden kaynaklandığına dikkat edin. .NET Framework’ü yükseltirken değil, yalnızca geliştirici araçlarını yükseltirken oluşur.|
|Öneri|Entity Framework hedef dosyaları, .NET Framework 4.6 sürümünden başlayarak yeni MSBuild düzeniyle çalışmak için düzeltildi. Bu Framework sürümüne yükseltmek bu sorunu çözecektir. Alternatif olarak, hedef dosyalarına doğrudan düzeltme eki uygulamak için [bu](http://stackoverflow.com/a/24249247/131944) geçici çözümü kullanabilirsiniz.|
|Kapsam|Ana|
|Sürüm|4.5.1|
|Tür|Yeniden Hedefleme|

