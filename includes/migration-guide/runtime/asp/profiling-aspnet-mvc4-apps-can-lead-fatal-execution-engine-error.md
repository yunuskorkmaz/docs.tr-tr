### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>ASP.Net MVC4 uygulamaları profil önemli yürütme altyapısı hatası yol açabilir

|   |   |
|---|---|
|Ayrıntılar|Profil oluşturucular NGEN/profile derlemeler kullanma başlangıçta durumla bir' önemli yürütme altyapısı' profili ASP.NET MVC4 uygulamalarının çökebilir|
|Öneri|.NET Framework 4.5.2 Bu sorun düzeltilmiştir. Alternatif olarak, profil oluşturucu bu sorunu belirterek önlemek <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> olay maske.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|

