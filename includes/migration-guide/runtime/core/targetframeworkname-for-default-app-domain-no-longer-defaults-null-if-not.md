### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>Null değilse ayarlamak için varsayılan uygulama etki alanı için TargetFrameworkName artık varsayılan olarak

|   |   |
|---|---|
|Ayrıntılar|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> Açıkça ayarlamadığınız sürece varsayılan uygulama etki alanında daha önce null idi. 4.6 içinde başlayan <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> özelliği varsayılan uygulama etki alanı için (varsa) TargetFrameworkAttribute türetilmiş bir varsayılan değer olacaktır. Varsayılan olmayan uygulama etki alanları devralmak devam edecek, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> (hangi 4.6 null varsayılan değil) varsayılan uygulama etki alanından, açıkça geçersiz kılınmadığı sürece.|
|Öneri|Kodu bağımlı değil için güncelleştirilmesi gerektiğini <xref:System.AppDomainSetup.TargetFrameworkName> null varsayılan olarak ayarlanıyor. Gerekirse bu özellik null olarak değerlendirilecek devam, onu açıkça bu değere ayarlanabilir.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|

