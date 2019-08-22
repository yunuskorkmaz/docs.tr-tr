---
title: <runtime> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
ms.openlocfilehash: 3cf99a4dcf64b82846729d8663e398385b7a1086
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663460"
---
# <a name="runtime-element"></a>\<çalışma zamanı > öğesi

Uygulamaları yapılandırmak için ortak dil çalışma zamanı tarafından kullanılan bilgileri sağlar.

\<Yapılandırma > \
\<çalışma zamanı >

## <a name="syntax"></a>Sözdizimi

```xml
<runtime>
</runtime>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki bölümlerde alt öğeler ve üst öğeler açıklanır.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<alwaysFlowImpersonationPolicy >](alwaysflowimpersonationpolicy-element.md)|Kimliğe bürünme işlemi ne olursa olsun, Windows kimliğinin her zaman zaman uyumsuz noktalarda akacağını belirtir.|
|[\<AppContextSwitchOverrides >](appcontextswitchoverrides-element.md)|Yeni işlevlere yönelik bir geri alma mekanizması sağlamak <xref:System.AppContext> için sınıfı tarafından kullanılan bir veya daha fazla anahtarı tanımlar.|
|[\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md)|İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisini sağlayan derlemeyi belirtir.|
|[\<appDomainManagerType >](appdomainmanagertype-element.md)|Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak hizmet veren türü belirtir.|
|[\<appDomainResourceMonitoring >](appdomainresourcemonitoring-element.md)|Çalışma zamanına, işlemin ömrü boyunca işlemdeki tüm uygulama etki alanlarında istatistikler toplamasını söyler.|
|[\<assemblyBinding >](assemblybinding-element-for-runtime.md)|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|
|[\<bypassTrustedAppStrongNames >](bypasstrustedappstrongnames-element.md)|Güvenilen derlemeler için tanımlayıcı ad doğrulamasının atlanıp atlanmayacağını belirtir.|
|[\<CompatSortNLSVersion >](compatsortnlsversion-element.md)|Çalışma zamanının, dize karşılaştırmaları gerçekleştirirken eski sıralama davranışını kullanması gerektiğini belirtir.|
|[\<developmentMode >](developmentmode-element.md)|Çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeleri arayıp aramayacağını belirtir.|
|[\<Disablecachingbindinghatalarıyla >](disablecachingbindingfailures-element.md)|.NET Framework sürüm 2,0 ' de varsayılan davranış olan bağlama hatalarının önbelleğe alınmasının devre dışı bırakılıp bırakılmadığını belirtir.|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|Bir iş parçacığı başlatıldığında tam iş parçacığı yığınının uygulanıp uygulanmadığını belirtir.|
|[\<disableFusionUpdatesFromADManager >](disablefusionupdatesfromadmanager-element.md)|Çalışma zamanı konağının bir uygulama etki alanı için yapılandırma ayarlarını geçersiz kılmasına izin vermek üzere varsayılan davranışın devre dışı bırakılıp bırakılmadığını belirtir.|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|Tarih ve saat ayrıştırma yöntemlerinin, yalnızca bir gün, ay, saat ve i/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanmış bir kural kümesi kullanıp kullanmadığını belirler.|
|[\<enforceFIPSPolicy >](enforcefipspolicy-element.md)|Şifreleme algoritmalarının Federal bilgi Işleme standartları (FIPS) ile uyumlu olması gereken bir bilgisayar yapılandırma gereksinimini zorlayamayacağını belirtir.|
|[\<etwEnable >](etwenable-element.md)|Ortak dil çalışma zamanı olayları için Windows için olay izlemenin (ETW) etkinleştirilip etkinleştirilmeyeceğini belirtir.|
|[\<forcePerformanceCounterUniqueSharedMemoryReads >](forceperformancecounteruniquesharedmemoryreads-element.md)|PerfCounter. dll ' nin, performans sayacı verilerinin kategoriye özgü paylaşılan bellekten veya genel bellekten yüklenip yüklenmeyeceğini belirleme .NET Framework sürüm 1,1 uygulamasında CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını belirtir.|
|[\<gcAllowVeryLargeObjects >](gcallowverylargeobjects-element.md)|64-bit platformlarda toplam boyutu 2 gigabayttan (GB) büyük olan dizileri etkinleştirir.|
|[\<gcConcurrent >](gcconcurrent-element.md)|Ortak dil çalışma zamanının çöp toplamayı eşzamanlı olarak çalıştırmasını belirtir.|
|[\<GCCpuGroup>](gccpugroup-element.md)|Çöp toplamanın birden çok CPU grubunu destekleyip desteklemediğini belirtir.|
|[\<gcServer >](gcserver-element.md)|Ortak dil çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.|
|[\<generatePublisherEvidence >](generatepublisherevidence-element.md)|Çalışma zamanının kod erişim güvenliği (CAS) Yayımcı ilkesini kullanıp kullanmadığını belirtir.|
|[\<Legacybozulmuş Tedstateexceptionspolicy >](legacycorruptedstateexceptionspolicy-element.md)|Çalışma zamanının yönetilen kodun erişim ihlallerini ve diğer bozuk durum özel durumlarını yakalayıp belirlemesine izin verip içermediğini belirtir.|
|[\<Legacyımpersonationpolicy >](legacyimpersonationpolicy-element.md)|Geçerli iş parçacığında yürütme bağlamı için akış ayarlarından bağımsız olarak, Windows kimliğinin zaman uyumsuz noktalarda akış yapmaz.|
|[\<loadfromRemoteSources >](loadfromremotesources-element.md)|Uzak kaynaklardaki derlemelerin tam güven olarak yüklenip yüklenmediğini belirtir.|
|[\<NetFx40_LegacySecurityPolicy >](netfx40-legacysecuritypolicy-element.md)|Çalışma zamanının eski kod erişim güvenliği (CAS) ilkesi kullanıp kullanmadığını belirtir.|
|[\<NetFx40_PInvokeStackResilience >](netfx40-pinvokestackresilience-element.md)|Çalışma zamanının, yönetilen ve yönetilmeyen kod arasındaki yavaş geçişlerin maliyetinde, çalışma zamanında hatalı platform çağırma bildirimlerini otomatik olarak düzeltilmediğini belirtir.|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Çalışma zamanının, <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemin karma kodlarını hesaplamak için sabit miktarda bellek kullanıp kullanmadığını belirtir.|
|[\<Tercihe bağlı Adofremoting >](prefercominsteadofmanagedremoting-element.md)|Çalışma zamanının, uygulama etki alanı sınırları arasında uzaktan iletişim yerine COM birlikte çalışabilirliğine sahip olacağını belirtir.|
|[\<relativeBindForResources >](relativebindforresources-element.md)|Uydu derlemeleri için araştırmayı iyileştirir.|
|[\<shadowCopyVerifyByTimeStamp >](shadowcopyverifybytimestamp-element.md)|Gölge kopyalamanın .NET Framework 4 ' te tanıtılan varsayılan başlangıç davranışını kullanıp kullanmadığını veya .NET Framework önceki sürümlerinin başlangıç davranışına geri dönmeyeceğini belirtir.|
|[\<Destek taşınabilirliği >](supportportability-element.md)|Bir uygulamanın, uygulama taşınabilirlik amaçları doğrultusunda derlemeleri eşdeğer olarak ele alan varsayılan davranışı devre dışı bırakarak, .NET Framework iki farklı uygulamasındaki aynı derlemeye başvurabildiklerini belirtir.|
|[\<System. Runtime. Caching >](system-runtime-caching-element-cache-settings.md)|Varsayılan bellek içi nesne önbelleğinde yapılandırma bilgileri sağlar.|
|[\<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md)|Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtıp dağıtmadığını belirtir.|
|[\<ThrowUnobservedTaskExceptions >](throwunobservedtaskexceptions-element.md)|İşlenmemiş görev özel durumlarının çalışan bir işlemi sonlandırmayı gerekip gerekmediğini belirtir.|
|[\<TimeSpan_LegacyFormatMode >](timespan-legacyformatmode-element.md)|Çalışma zamanının değerler için <xref:System.TimeSpan> eski biçimlendirmeyi kullanıp kullanmadığını belirtir.|
|[\<useLegacyJit >](uselegacyjit-element.md)|Ortak dil çalışma zamanının, Just-In-Time derlemesi için eski 64-bit JıT derleyicisini kullanıp kullanmadığını belirler.|
|[\<UseRandomizedStringHashAlgorithm >](userandomizedstringhashalgorithm-element.md)|Çalışma zamanının, her uygulama etki alanı temelinde dizeler için karma kodları hesaplayıp hesaplamadığını belirtir.|
|[\<Usesmallınternalthreadyığınları >](usesmallinternalthreadstacks-element.md)|Çalışma zamanının, varsayılan yığın boyutu yerine dahili olarak kullandığı belirli iş parçacıklarını oluştururken açık yığın boyutlarını kullanmasını ister.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|

## <a name="remarks"></a>Açıklamalar

Bir yapılandırma dosyasının [ \<Runtime >](runtime-element.md) bölümündeki alt öğeler, bir uygulamanın nasıl yürütüldüğünü yapılandırmak için ortak dil çalışma zamanı tarafından kullanılır. Örneğin, [ \<gcServer >](gcserver-element.md) öğesi çöp toplayıcının iş istasyonu atık toplama veya sunucu [ \<](userandomizedstringhashalgorithm-element.md) çöp toplama, UseRandomizedStringHashAlgorithm > öğesi kullanıp kullanmadığını belirler ortak dil çalışma zamanının, bir uygulama başına ya da uygulama başına etki alanı temelinde dize için karma kodlarını hesaplayıp hesaplamadığını ve `AppContextSwitchOverrides` bu öğe, kitaplık kullanıcılarının bir kitaplık tarafından sunulan değiştirilen işlevselliği kabul etmesine veya devre dışı bırakmanıza olanak tanır.

Çalışma zamanı > bölümündeki öğeler [ \<](runtime-element.md) , uygulama başlangıcında ortak dil çalışma zamanı tarafından otomatik olarak okunurdur. Ayrıca, varsayılan olmayan bir uygulama etki alanı için yapılandırma dosyasını <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> özelliği adına sağlayarak tanımlayabilirsiniz; uygulama etki alanı yüklendiğinde ayarları otomatik olarak okunabilir. Mümkünse, uygulamanızın yapılandırma dosyasındaki [ \<çalışma zamanı >](runtime-element.md) bölümünde ayarları doğrudan okumanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
