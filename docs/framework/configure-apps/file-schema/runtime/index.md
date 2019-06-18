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
ms.openlocfilehash: d22046393b22683b961f5da7a5623f5dfa6a702e
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170026"
---
# <a name="runtime-settings-schema"></a>Çalışma Zamanı Ayarları Şeması

Çalışma zamanı ayarları, .NET Framework'ü hedefleyen uygulamaları yapılandırmak için ortak dil çalışma zamanı tarafından kullanılır.

## <a name="the-runtime-section-and-its-parent-and-child-elements"></a>\<Çalışma zamanı > bölüm ve onun üst ve alt öğeleri

[\<Yapılandırma >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)\
&nbsp;&nbsp;[\<çalışma zamanı >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Alwaysflowımpersonationpolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<AppContextSwitchOverrides >](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainResourceMonitoring >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyBinding >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<dependentAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyIdentity >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblyidentity-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<bindingRedirect >](../../../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<codeBase>](../../../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<yoklama >](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<publisherPolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<qualifyAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<developmentMode >](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCachingBindingFailures >](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableFusionUpdatesFromADManager >](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<EnableAmPmParseAdjustment >](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Enforcefıpspolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<etwEnable >](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcAllowVeryLargeObjects >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcConcurrent >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<generatePublisherEvidence >](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyCorruptedStateExceptionsPolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Legacyımpersonationpolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<loadfromRemoteSources >](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_LegacySecurityPolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Prefercomınsteadofmanagedremoting >](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<relativeBindForResources >](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<shadowCopyVerifyByTimeStamp >](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<supportPortability >](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<System.Runtime.Caching >](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<Temizleme >](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<ThrowUnobservedTaskExceptions >](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<useLegacyJit >](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseRandomizedStringHashAlgorithm >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Usesmallınternalthreadstacks >](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)\
&nbsp;&nbsp;\<\runtime > \
\<\Configuration >

## <a name="alphabetical-list-of-runtime-elements"></a>Alfabetik listesi \<çalışma zamanı > öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|Adlandırılmış bir önbelleğe ekler `namedCaches` koleksiyonu için bir önbellek.|
|[\<Alwaysflowımpersonationpolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|Windows kimlik her zaman arasında nasıl kimliğe bürünme gerçekleştirilip gerçekleştirilmediğine bakılmaksızın zaman uyumsuz noktalar, akışları olduğunu belirtir.|
|[\<AppContextSwitchOverrides >](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|Tarafından kullanılan bir veya daha fazla anahtarları tanımlar <xref:System.AppContext> yeni işlevselliği için bir geri çevirme mekanizma sağlar sınıfını.|
|[\<appDomainManagerAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|Varsayılan uygulama etki alanı işlemde uygulama etki alanı yöneticisi sağlayan derlemeyi belirtir.|
|[\<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak görev yapan türünü belirtir.|
|[\<appDomainResourceMonitoring >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|Ömür işlemin işlemdeki tüm uygulama etki alanlarında istatistikleri toplamak için çalışma zamanı bildirir.|
|[\<assemblyBinding >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|
|[\<assemblyIdentity >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblyidentity-element-for-runtime.md)|Bir derlemeyle ilgili tanımlayıcı bilgiler içerir.|
|[\<bindingRedirect >](../../../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)|Bir derleme sürümünü diğerine yeniden yönlendirir.|
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|Güvenilir derlemeler için tanımlayıcı ad doğrulaması atlanmasına olup olmadığını belirtir.|
|[\<Temizleme >](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|Temizler `namedCaches` koleksiyonu için bir önbellek.|
|[\<codeBase>](../../../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)|Çalışma zamanının bir derlemeyi nerede belirtir.|
|[\<CompatSortNLSVersion >](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|Çalışma zamanı dize karşılaştırmaları yaparken eski sıralama davranışını kullanmalısınız belirtir|
|[\<dependentAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.|
|[\<developmentMode >](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|Çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinleri arar olup olmadığını belirtir.|
|[\<disableCachingBindingFailures >](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|Bağlama hataları .NET Framework 2. 0'de varsayılan davranışı olan önbelleğe almayı devre dışı bırakılıp bırakılmadığını belirtir.|
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|Bir iş parçacığı başladığında iş parçacığı yığınının tamamının taahhüt olup olmadığını belirtir.|
|[\<disableFusionUpdatesFromADManager >](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|Uygulama etki alanı için yapılandırma ayarlarını geçersiz kılmak çalışma zamanı ana bilgisayarı izin vermek için varsayılan davranışı devre dışı bırakılıp bırakılmadığını belirtir.|
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|Tarih ve saat yöntemleri ayrıştırma ayarlanmış bir kural kümesi yalnızca bir gün, ay, saat ve AM/PM göstergesi içeren tarih dizeleri ayrıştırılacak kullanıp kullanmadığını belirler.|
|[\<Enforcefıpspolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|Şifreleme algoritmaları Federal Bilgi işleme standartları (FIPS ile) uyması gereken bir bilgisayar yapılandırma gereksinimini zorlanıp zorlanmayacağını belirtir.|
|[\<etwEnable >](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|Olay İzleme (ETW) Windows için ortak dil çalışma zamanı olayları için etkinleştirilip etkinleştirilmeyeceğini belirtir.|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|PerfCounter.dll CategoryOptions kayıt defteri ayarı bir .NET Framework sürüm 1.1 uygulamasında kategoriye özgü paylaşılan bellek ya da genel bellek performans sayacı verilerini yüklemek karar vermek için kullanıp kullanmayacağını belirtir.|
|[\<gcAllowVeryLargeObjects >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|64-bit platformlarda toplam boyutu 2 gigabayttan (GB) büyük olan dizileri etkinleştirir.|
|[\<gcConcurrent >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|Çalışma zamanının atık toplama eşzamanlı olarak çalışıp çalışmayacağını belirtir.|
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|Çöp toplama, birden fazla CPU grubu destekleyip desteklemediğini belirtir.|
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|Ortak dil çalışma zamanı sunucu çöp toplama çalışıp çalışmayacağını belirtir.|
|[\<generatePublisherEvidence >](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|Çalışma zamanı kod erişim güvenliği (CAS) Yayımcı ilkesi kullanıp kullanmayacağını belirtir.|
|[\<legacyCorruptedStateExceptionsPolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|Erişim ihlalleri ve diğer bozuk durum özel durumları yakalamak yönetilen kod çalışma zamanı izin verip vermediğini belirtir.|
|[\<Legacyımpersonationpolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Windows kimliği, geçerli iş parçacığı üzerindeki yürütme içeriği için akış ayarlarından bağımsız olarak zaman uyumsuz noktalar arasında geçmeyen belirtir.|
|[\<loadfromRemoteSources >](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|Uzak kaynaktan derlemeleri tam güven yüklü olup olmadığını belirtir.|
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Temel alan bir önbellek yapılandırmak için kullanılan bir öğe tanımlar <xref:System.Runtime.Caching.MemoryCache> sınıfı.|
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Yapılandırma ayarları koleksiyonu içeren `namedCache` örneği.|
|[\<NetFx40_LegacySecurityPolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|Çalışma zamanının eski kod erişimi güvenliği (CAS) ilkesi kullanıp kullanmayacağını belirtir.|
|[\<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|Olup çalışma zamanı düzeltmeleri yanlış platform çağırma bildirimler arasında yavaş geçişler, çalışma zamanında otomatik olarak yönetilen ve yönetilmeyen kod belirtir.|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Çalışma zamanı için karma kodları hesaplamak üzere sabit miktarda bellek kullanıp kullanmayacağını belirtir <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi.|
|[\<PreferComInsteadOfManagedRemoting>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|Çalışma zamanı uygulama etki alanı sınırları uzaktan iletişim yerine COM birlikte çalışma kullanacağını belirtir.|
|[\<yoklama >](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|Çalışma zamanı derlemeleri yüklenirken arama alt dizinleri belirtir.|
|[\<publisherPolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|Çalışma zamanı Yayımcı ilkesi uygulanıp uygulanmayacağını belirtir.|
|[\<qualifyAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|Kısmi bir adı kullanıldığında dinamik olarak yüklenmesi gereken bütünleştirilmiş kodun tam adını belirtir.|
|[\<relativeBindForResources >](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|Araştırma için uydu derlemelerini en iyi duruma getirir.|
|[\<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|Bir adlandırılmış önbellek girişi kaldırır `namedCaches` koleksiyonu için bir önbellek.|
|[\<çalışma zamanı >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|Derleme bağlama ve atık toplama davranışı hakkında bilgi içerir.|
|[\<shadowCopyTimeStampVerification >](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|Gölge kopyalama .NET Framework 4'te sunulan varsayılan başlangıç davranışını kullanıp kullanmayacağını belirtir ve .NET Framework'ün önceki sürümlerinde başlangıç davranışını geri döner.|
|[\<supportPortability >](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|Bir uygulama derlemeleri uygulama taşınabilirliği amacıyla eşdeğer kabul eder varsayılan davranışı devre dışı bırakarak aynı derlemenin iki farklı uygulamalarında .NET Framework'ün başvurabileceğini belirtir.|
|[\<System.Runtime.Caching >](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Varsayılan bellek içi nesne önbelleği için yapılandırma bilgileri sağlar.|
|[\<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtmadığını belirtir.|
|[\<ThrowUnobservedTaskExceptions >](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|Çalışan bir işleme, işlenmemiş bir görev özel durumlarını sonlandırma olup olmadığını belirtir.|
|[\<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|Çalışma zamanı için eski biçimlendirme kullanıp kullanmayacağını belirtir <xref:System.TimeSpan> değerleri.|
|[\<useLegacyJit >](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|Ortak dil çalışma zamanı için tam zamanında derleme eski 64 bit JIT Derleyici kullanıp kullanmadığını belirler.|
|[\<UseRandomizedStringHashAlgorithm >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|Çalışma zamanı için dizelerin karma kodlarını hesaplayıp belirtir bir her uygulama etki alanı.|
|[\<Usesmallınternalthreadstacks >](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|İstekleri, belirli iş parçacıklarını oluşturduğunda, çalışma zamanı açık yığın boyutlarını kullanmak yerine varsayılan yığın boyutu dahili olarak kullanır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Eş zamanlı çöp toplama devre dışı bırakmak için](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
