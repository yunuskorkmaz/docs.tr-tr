### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>Null değilse ayarlamak için TargetFrameworkName varsayılan uygulama etki alanı için artık varsayılan olarak

|   |   |
|---|---|
|Ayrıntılar|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> Açıkça ayarlamadığınız sürece varsayılan uygulama etki alanında daha önce null idi. 4.6 içinde başlayarak <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> özelliği varsayılan uygulama etki alanı için (varsa) TargetFrameworkAttribute türetilmiş bir varsayılan değer olacaktır. Varsayılan olmayan uygulama etki alanları devralacak şekilde devam edecek kendi <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> (hangi 4.6 null varsayılan değil) varsayılan uygulama etki alanından açıkça kılınmadığı sürece.|
|Öneri|Kodu bağımlı değil için güncelleştirilmesi gerektiğini <xref:System.AppDomainSetup.TargetFrameworkName> null varsayılan olarak ayarlanıyor. Bu değer gerekirse bu özellik null olarak değerlendirilecek devam ettiğinden, onu açıkça bu değer için ayarlanabilir.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|

