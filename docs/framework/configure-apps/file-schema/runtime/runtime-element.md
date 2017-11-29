---
title: "&lt;çalışma zamanı&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
caps.latest.revision: "70"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c4c64de42f82590e1e8dc24afa46f66c3efb35b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltruntimegt-element"></a>&lt;çalışma zamanı&gt; öğesi
Uygulamaları yapılandırmak için ortak dil çalışma zamanı tarafından kullanılan bilgileri sağlar.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<runtime>  
</runtime>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde, alt öğelerinin ve üst öğenin açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Alwaysflowımpersonationpolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|Windows Identity her zaman kimliğe bürünme nasıl gerçekleştirildiği bağımsız olarak zaman uyumsuz noktaları arasında akan olduğunu belirtir.|  
|[\<AppContextSwitchOverrides >](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|Tarafından kullanılan bir veya daha fazla anahtarları tanımlar <xref:System.AppContext> sınıfı yeni işlevsellik için vazgeçme mekanizma sağlar.|  
|[\<appDomainManagerAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|İşlem varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi sağlar derleme belirtir.|  
|[\<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak görev yapar türünü belirtir.|  
|[\<appDomainResourceMonitoring >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|İşlem ömrü için işlemdeki tüm uygulama etki alanları istatistikleri toplamak için çalışma zamanı bildirir.|  
|[\<assemblyBinding >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|  
|[\<bypassTrustedAppStrongNames >](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|Güçlü ad doğrulaması güvenilir derlemeler için atlanır olup olmadığını belirtir.|  
|[\<CompatSortNLSVersion >](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|Çalışma zamanı eski sıralama davranışı dize karşılaştırmaları gerçekleştirirken kullanması gerektiğini belirtir.|  
|[\<developmentMode >](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|Çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinde arar olup olmadığını belirtir.|  
|[\<disableCachingBindingFailures >](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|Bağlama hataları .NET Framework sürüm 2.0 varsayılan davranışı olan önbelleğe almayı devre dışı olup olmadığını belirtir.|  
|[\<disableCommitThreadStack >](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|Bir iş parçacığı başlatıldığında tam iş parçacığı yığın kaydedilmiş olup olmadığını belirtir.|  
|[\<disableFusionUpdatesFromADManager >](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|Uygulama etki alanı için yapılandırma ayarlarını geçersiz kılmak çalışma zamanı konak izin vermek için varsayılan davranışı devre dışı olup olmadığını belirtir.|  
|[\<EnableAmPmParseAdjustment >](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|Tarih ve saat yöntemleri ayrıştırma bir ayarlanmış kuralları kümesi yalnızca bir gün, ay, saat ve AM/PM Belirleyicisi içeren tarih dizeleri ayrıştırmak için kullanılabilir olup olmadığını belirler.|  
|[\<Enforcefıpspolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|Şifreleme algoritmaları Federal Bilgi işleme standartları (FIPS ile) uymalıdır bir bilgisayar yapılandırmasını gereksinim zorlanıp zorlanmayacağını belirtir.|  
|[\<etwEnable >](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|Olay izleme için ortak dil çalışma zamanı olayları Windows (ETW) etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads >](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|PerfCounter.dll CategoryOptions kayıt defteri ayarını bir .NET Framework sürüm 1.1 uygulamasında kategoriye özel paylaşılan bellek ya da genel bellek performans sayacı verilerini yüklemeye karar vermek için kullanıp kullanmadığını belirtir.|  
|[\<gcAllowVeryLargeObjects >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|64-bit platformlarda toplam boyutu 2 gigabayttan (GB) büyük olan dizileri etkinleştirir.|  
|[\<gcConcurrent >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|Ortak dil çalışma zamanı çöp toplama eşzamanlı olarak çalışıp çalışmayacağını belirtir.|  
|[\<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|Çöp toplama birden çok CPU grupları destekleyip desteklemediğini belirtir.|  
|[\<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|Ortak dil çalışma zamanı sunucu çöp toplama çalışıp çalışmayacağını belirtir.|  
|[\<generatePublisherEvidence >](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|Çalışma zamanı kod erişim güvenliği (CAS) Yayımcı ilkesi kullanıp kullanmadığını belirtir.|  
|[\<legacyCorruptedStateExceptionsPolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|Çalışma zamanı erişim ihlalleri ve diğer bozuk durumda özel durumları yakalamak yönetilen kod izin verip vermeyeceğini belirtir.|  
|[\<Legacyımpersonationpolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Windows Identity geçerli iş parçacığı üzerinde yürütme bağlamı akış ayarlarına bakılmaksızın zaman uyumsuz noktaları arasında akışını değil belirtir.|  
|[\<loadfromRemoteSources >](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|Uzak kaynaklardan derlemeler tam güven yüklü olup olmadığını belirtir.|  
|[< NetFx40_LegacySecurityPolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|Çalışma zamanı eski kod erişim güvenliği (CAS) ilkesi kullanıp kullanmadığını belirtir.|  
|[< Netfx40_pınvokestackresilience >](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|Olup çalışma zamanı düzeltmeleri yanlış platform çağırma bildirimler arasında yavaş geçişler, çalışma zamanında otomatik olarak yönetilen ve yönetilmeyen kod belirtir.|  
|[< NetFx45_CultureAwareComparerGetHashCode_LongStrings >](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Çalışma zamanı için karma kodları hesaplamak için sabit miktarlı bellek kullanıp kullanmadığını belirtir <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi.|  
|[\<PreferComInsteadOfRemoting >](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|Çalışma zamanı uygulama etki alanı sınırlarında yerine remoting COM birlikte çalışma kullanacağını belirtir.|  
|[\<relativeBindForResources >](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|Araştırması için uydu derlemelerini en iyi duruma getirir.|  
|[\<shadowCopyVerifyByTimeStamp >](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|Gölge kopyalama sunulan varsayılan başlangıç davranışını kullanıp kullanmadığını belirtir [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], veya .NET Framework'ün önceki sürümlerinde başlangıç davranışını döner.|  
|[\<supportPortability >](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|Bir uygulama aynı bütünleştirilmiş kodda iki farklı uygulamaları .NET Framework'ün derlemeleri uygulama taşınabilirliği amacıyla eşdeğer olarak davranır varsayılan davranışı devre dışı bırakarak başvurabilir belirtir.|  
|[\<System.Runtime.Caching >](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Varsayılan bellek içi nesne önbelleği için yapılandırma bilgilerini sağlar.|  
|[< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|Çalışma zamanı, tüm CPU gruplarında yönetilen iş parçacığı dağıtır olup olmadığını belirtir.|  
|[\<ThrowUnobservedTaskExceptions >](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|İşlenmemiş görev özel durumlarını çalışan bir işlemi sonlandırmak olup olmadığını belirtir.|  
|[< TimeSpan_LegacyFormatMode >](../../../../../docs/framework/configure-apps/file-schema/runtime/timespan-legacyformatmode-element.md)|Çalışma zamanı için eski biçimlendirme kullanıp kullanmadığını belirtir <xref:System.TimeSpan> değerleri.|  
|[\<useLegacyJit >](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|Ortak dil çalışma zamanı için tam zamanında derleme eski 64-bit JIT Derleyici kullanıp kullanmadığını belirler.|  
|[\<UseRandomizedStringHashAlgorithm >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|Çalışma zamanı üzerinde karma kodlarını dizeleri hesaplar olup olmadığını belirten bir uygulama etki alanı temelinde.|  
|[\<Usesmallınternalthreadstacks >](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|İstekler, belirli iş parçacıklarını oluşturduğunda, çalışma zamanı açık yığın boyutları kullanmak yerine varsayılan yığın boyutunu dahili olarak kullanır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 Alt öğeleri [ \<çalışma zamanı >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) yapılandırma dosyasının bir uygulamanın nasıl yürütür yapılandırmak için ortak dil çalışma zamanı tarafından kullanılır. Örneğin, [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) öğesi belirler atık toplayıcı iş istasyonu çöp toplama veya sunucu çöp toplama, kullanıp kullanmadığını [ \< UseRandomizedStringHashAlgorithm >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md) öğesi ortak dil çalışma zamanı bir uygulama başına veya uygulama başına etki alanı temelinde dizesi için karma kodları hesaplar olup olmadığını belirler ve `AppContextSwitchOverrides` öğesi kitaplığı kullanıcıları sağlar kabul veya bir kitaplık tarafından sağlanan değiştirilmiş işlevselliği dışında opt için.  
  
 Öğeleri [ \<çalışma zamanı >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölüm okunur otomatik olarak uygulama başlangıcında ortak dil çalışma zamanı tarafından. Adının sağlayarak bir varsayılan olmayan uygulama etki alanı için yapılandırma dosyası tanımlayabilirsiniz <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> özellik; uygulama etki alanı zaman yüklendi ayarlarını otomatik olarak okunur. Şimdiye kadar doğrudan ayarlarında okuma gerek nadiren, olmalıdır [ \<çalışma zamanı >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulamanızın yapılandırma dosyasına bölümünde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma dosyası şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
