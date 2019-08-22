---
title: Çalışma Zamanı Ayarları Şeması
ms.date: 03/30/2017
helpviewer_keywords:
- schema runtime settings
- configuration schema [.NET Framework], runtime settings
- runtime settings schema
ms.assetid: f04816ab-110d-4e28-9283-845d6d9a4a68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66fef76e684fb2bc0c497a695919e82750c17df8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663639"
---
# <a name="runtime-settings-schema"></a>Çalışma Zamanı Ayarları Şeması

Çalışma zamanı ayarları, .NET Framework hedefleyen uygulamaları yapılandırmak için ortak dil çalışma zamanı tarafından kullanılır.

## <a name="the-runtime-section-and-its-parent-and-child-elements"></a>\<Çalışma zamanı > bölümü ve üst ve alt öğeleri

[\<Yapılandırma >](../configuration-element.md)\
&nbsp;&nbsp;[\<çalışma zamanı >](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<alwaysFlowImpersonationPolicy >](alwaysflowimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<AppContextSwitchOverrides >](appcontextswitchoverrides-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerType >](appdomainmanagertype-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainResourceMonitoring >](appdomainresourcemonitoring-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyBinding >](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<dependentAssembly >](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<AssemblyIdentity >](assemblyidentity-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<bindingRedirect >](bindingredirect-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<Kod temeli >](codebase-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<yoklama >](probing-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<publisherPolicy >](publisherpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<qualifyAssembly >](qualifyassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<bypassTrustedAppStrongNames >](bypasstrustedappstrongnames-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<CompatSortNLSVersion >](compatsortnlsversion-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<developmentMode >](developmentmode-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Disablecachingbindinghatalarıyla >](disablecachingbindingfailures-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCommitThreadStack >](disablecommitthreadstack-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableFusionUpdatesFromADManager >](disablefusionupdatesfromadmanager-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Enableampmparseayarlaması >](enableampmparseadjustment-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<enforceFIPSPolicy >](enforcefipspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<etwEnable >](etwenable-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<forcePerformanceCounterUniqueSharedMemoryReads >](forceperformancecounteruniquesharedmemoryreads-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcAllowVeryLargeObjects >](gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcConcurrent >](gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCCpuGroup >](gccpugroup-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcServer >](gcserver-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<generatePublisherEvidence >](generatepublisherevidence-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Legacybozulmuş Tedstateexceptionspolicy >](legacycorruptedstateexceptionspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Legacyımpersonationpolicy >](legacyimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<loadfromRemoteSources >](loadfromremotesources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_LegacySecurityPolicy >](netfx40-legacysecuritypolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_PInvokeStackResilience >](netfx40-pinvokestackresilience-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >](netfx45-cultureawarecomparergethashcode-longstrings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<PreferComInsteadOfManagedRemoting >](prefercominsteadofmanagedremoting-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<relativeBindForResources >](relativebindforresources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<shadowCopyVerifyByTimeStamp >](shadowcopyverifybytimestamp-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Destek taşınabilirliği >](supportportability-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<System. Runtime. Caching >](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<memoryCache >](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<Namedönbellekler >](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<> Ekle](add-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<> Temizle](clear-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<> Kaldır](remove-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<ThrowUnobservedTaskExceptions >](throwunobservedtaskexceptions-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<TimeSpan_LegacyFormatMode >](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<useLegacyJit >](uselegacyjit-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseRandomizedStringHashAlgorithm >](userandomizedstringhashalgorithm-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Usesmallınternalthreadyığınları >](usesmallinternalthreadstacks-element.md)\
&nbsp;&nbsp;\<\runtime > \
\<\configuration >

## <a name="alphabetical-list-of-runtime-elements"></a>\<Çalışma zamanı > öğelerinin alfabetik listesi

|Öğe|Açıklama|
|-------------|-----------------|
|[\<> Ekle](add-element-for-namedcaches.md)|Bir bellek önbelleği için `namedCaches` koleksiyona adlandırılmış bir önbellek ekler.|
|[\<alwaysFlowImpersonationPolicy >](alwaysflowimpersonationpolicy-element.md)|Kimliğe bürünme işlemi ne olursa olsun, Windows kimliğinin her zaman zaman uyumsuz noktalarda akacağını belirtir.|
|[\<AppContextSwitchOverrides >](appcontextswitchoverrides-element.md)|Yeni işlevlere yönelik bir geri alma mekanizması sağlamak <xref:System.AppContext> için sınıfı tarafından kullanılan bir veya daha fazla anahtarı tanımlar.|
|[\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md)|İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisini sağlayan derlemeyi belirtir.|
|[\<appDomainManagerType >](appdomainmanagertype-element.md)|Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak hizmet veren türü belirtir.|
|[\<appDomainResourceMonitoring >](appdomainresourcemonitoring-element.md)|Çalışma zamanına, işlemin ömrü boyunca işlemdeki tüm uygulama etki alanlarında istatistikler toplamasını söyler.|
|[\<assemblyBinding >](assemblybinding-element-for-runtime.md)|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|
|[\<AssemblyIdentity >](assemblyidentity-element-for-runtime.md)|Bir derlemeyle ilgili tanımlama bilgilerini içerir.|
|[\<bindingRedirect >](bindingredirect-element.md)|Bir derleme sürümünü diğerine yeniden yönlendirir.|
|[\<bypassTrustedAppStrongNames >](bypasstrustedappstrongnames-element.md)|Güvenilen derlemeler için tanımlayıcı ad doğrulamasının atlanıp atlanmayacağını belirtir.|
|[\<> Temizle](clear-element-for-namedcaches.md)|Bir bellek önbelleğinin koleksiyonunu temizler. `namedCaches`|
|[\<Kod temeli >](codebase-element.md)|Çalışma zamanının bir derlemeyi bulabilecekleri yeri belirtir.|
|[\<CompatSortNLSVersion >](compatsortnlsversion-element.md)|Çalışma zamanının, dize karşılaştırmaları gerçekleştirirken eski sıralama davranışını kullanması gerektiğini belirtir|
|[\<dependentAssembly >](dependentassembly-element.md)|Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.|
|[\<developmentMode >](developmentmode-element.md)|Çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeleri arayıp aramayacağını belirtir.|
|[\<Disablecachingbindinghatalarıyla >](disablecachingbindingfailures-element.md)|.NET Framework 2,0 ' de varsayılan davranış olan bağlama hatalarının önbelleğe alınmasının devre dışı bırakılıp bırakılmadığını belirtir.|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|Bir iş parçacığı başlatıldığında tam iş parçacığı yığınının uygulanıp uygulanmadığını belirtir.|
|[\<disableFusionUpdatesFromADManager >](disablefusionupdatesfromadmanager-element.md)|Çalışma zamanı konağının bir uygulama etki alanı için yapılandırma ayarlarını geçersiz kılmasına izin vermek üzere varsayılan davranışın devre dışı bırakılıp bırakılmadığını belirtir.|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|Tarih ve saat ayrıştırma yöntemlerinin, yalnızca bir gün, ay, saat ve i/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanmış bir kural kümesi kullanıp kullanmadığını belirler.|
|[\<enforceFIPSPolicy >](enforcefipspolicy-element.md)|Şifreleme algoritmalarının Federal bilgi Işleme standartları (FIPS) ile uyumlu olması gereken bir bilgisayar yapılandırma gereksinimini zorlayamayacağını belirtir.|
|[\<etwEnable >](etwenable-element.md)|Ortak dil çalışma zamanı olayları için Windows için olay izlemenin (ETW) etkinleştirilip etkinleştirilmeyeceğini belirtir.|
|[\<forcePerformanceCounterUniqueSharedMemoryReads >](forceperformancecounteruniquesharedmemoryreads-element.md)|PerfCounter. dll ' nin, performans sayacı verilerinin kategoriye özgü paylaşılan bellekten veya genel bellekten yüklenip yüklenmeyeceğini belirleme .NET Framework sürüm 1,1 uygulamasında CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını belirtir.|
|[\<gcAllowVeryLargeObjects >](gcallowverylargeobjects-element.md)|64-bit platformlarda toplam boyutu 2 gigabayttan (GB) büyük olan dizileri etkinleştirir.|
|[\<gcConcurrent >](gcconcurrent-element.md)|Çalışma zamanının çöp toplamayı eşzamanlı olarak çalıştırmasını belirtir.|
|[\<GCCpuGroup>](gccpugroup-element.md)|Çöp toplamanın birden çok CPU grubunu destekleyip desteklemediğini belirtir.|
|[\<gcServer >](gcserver-element.md)|Ortak dil çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.|
|[\<generatePublisherEvidence >](generatepublisherevidence-element.md)|Çalışma zamanının kod erişim güvenliği (CAS) Yayımcı ilkesini kullanıp kullanmadığını belirtir.|
|[\<Legacybozulmuş Tedstateexceptionspolicy >](legacycorruptedstateexceptionspolicy-element.md)|Çalışma zamanının yönetilen kodun erişim ihlallerini ve diğer bozuk durum özel durumlarını yakalayıp belirlemesine izin verip içermediğini belirtir.|
|[\<Legacyımpersonationpolicy >](legacyimpersonationpolicy-element.md)|Geçerli iş parçacığında yürütme bağlamı için akış ayarlarından bağımsız olarak, Windows kimliğinin zaman uyumsuz noktalarda akış yapmaz.|
|[\<loadfromRemoteSources >](loadfromremotesources-element.md)|Uzak kaynaklardaki derlemelerin tam güven olarak yüklenip yüklenmediğini belirtir.|
|[\<memoryCache >](memorycache-element-cache-settings.md)|<xref:System.Runtime.Caching.MemoryCache> Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar.|
|[\<Namedönbellekler >](namedcaches-element-cache-settings.md)|`namedCache` Örnek için yapılandırma ayarlarının bir koleksiyonunu içerir.|
|[\<NetFx40_LegacySecurityPolicy >](netfx40-legacysecuritypolicy-element.md)|Çalışma zamanının eski kod erişim güvenliği (CAS) ilkesi kullanıp kullanmadığını belirtir.|
|[\<NetFx40_PInvokeStackResilience >](netfx40-pinvokestackresilience-element.md)|Çalışma zamanının, yönetilen ve yönetilmeyen kod arasındaki yavaş geçişlerin maliyetinde, çalışma zamanında hatalı platform çağırma bildirimlerini otomatik olarak düzeltilmediğini belirtir.|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Çalışma zamanının, <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemin karma kodlarını hesaplamak için sabit miktarda bellek kullanıp kullanmadığını belirtir.|
|[\<PreferComInsteadOfManagedRemoting>](prefercominsteadofmanagedremoting-element.md)|Çalışma zamanının, uygulama etki alanı sınırları arasında uzaktan iletişim yerine COM birlikte çalışabilirliğine sahip olacağını belirtir.|
|[\<yoklama >](probing-element.md)|Derlemeler yüklenirken çalışma zamanının aradığı alt dizinleri belirtir.|
|[\<publisherPolicy >](publisherpolicy-element.md)|Çalışma zamanının yayımcı ilkesi uygulanıp uygulanmadığını belirtir.|
|[\<qualifyAssembly >](qualifyassembly-element.md)|Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.|
|[\<relativeBindForResources >](relativebindforresources-element.md)|Uydu derlemeleri için araştırmayı iyileştirir.|
|[\<> Kaldır](remove-element-for-namedcaches.md)|Bir bellek önbelleği için `namedCaches` koleksiyondan adlandırılmış bir önbellek girdisini kaldırır.|
|[\<çalışma zamanı >](runtime-element.md)|Derleme bağlaması ve çöp toplamanın davranışı hakkında bilgi içerir.|
|[\<Shadowcopytimestampdoğrulaması >](shadowcopyverifybytimestamp-element.md)|Gölge kopyalamanın .NET Framework 4 ' te tanıtılan varsayılan başlangıç davranışını kullanıp kullanmadığını veya .NET Framework önceki sürümlerinin başlangıç davranışına geri dönmeyeceğini belirtir.|
|[\<Destek taşınabilirliği >](supportportability-element.md)|Bir uygulamanın, uygulama taşınabilirlik amaçları doğrultusunda derlemeleri eşdeğer olarak ele alan varsayılan davranışı devre dışı bırakarak, .NET Framework iki farklı uygulamasındaki aynı derlemeye başvurabildiklerini belirtir.|
|[\<System. Runtime. Caching >](system-runtime-caching-element-cache-settings.md)|Varsayılan bellek içi nesne önbelleğinde yapılandırma bilgileri sağlar.|
|[\<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md)|Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtıp dağıtmadığını belirtir.|
|[\<ThrowUnobservedTaskExceptions >](throwunobservedtaskexceptions-element.md)|İşlenmemiş görev özel durumlarının çalışan bir işlemi sonlandırmayı gerekip gerekmediğini belirtir.|
|[\<TimeSpan_LegacyFormatMode >](runtime-element.md)|Çalışma zamanının değerler için <xref:System.TimeSpan> eski biçimlendirmeyi kullanıp kullanmadığını belirtir.|
|[\<useLegacyJit >](uselegacyjit-element.md)|Ortak dil çalışma zamanının, Just-In-Time derlemesi için eski 64-bit JıT derleyicisini kullanıp kullanmadığını belirler.|
|[\<UseRandomizedStringHashAlgorithm >](userandomizedstringhashalgorithm-element.md)|Çalışma zamanının, her uygulama etki alanı temelinde dizeler için karma kodları hesaplayıp hesaplamadığını belirtir.|
|[\<Usesmallınternalthreadyığınları >](usesmallinternalthreadstacks-element.md)|Çalışma zamanının, varsayılan yığın boyutu yerine dahili olarak kullandığı belirli iş parçacıklarını oluştururken açık yığın boyutlarını kullanmasını ister.|

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyası Şeması](../index.md)
- [Eşzamanlı atık toplamayı devre dışı bırakmak için](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../redirect-assembly-versions.md)
