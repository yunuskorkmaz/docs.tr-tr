### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>ASP.Net MVC4 uygulamaları profil oluşturma için önemli yürütme altyapısı hata neden olabilir

|   |   |
|---|---|
|Ayrıntılar|NGEN/profile bütünleştirilmiş kodları kullanarak profil oluşturucular başlangıçta 'Önemli yürütme altyapısı bir özel durum' ile profili oluşturulmuş ASP.NET MVC4 uygulamalarının çökebilir|
|Öneri|.NET Framework 4.5.2 Bu sorun düzeltilmiştir. Alternatif olarak, profil oluşturucu bu sorunu belirterek önlemek <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> kendi olay maske.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|

