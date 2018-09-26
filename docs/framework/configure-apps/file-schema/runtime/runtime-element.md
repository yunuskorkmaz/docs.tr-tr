---
title: '&lt;çalışma zamanı&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0640b4c54b6f1429bce4947ec536352f240ca719
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208652"
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
 Alt öğeler ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Alwaysflowımpersonationpolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|Windows kimlik her zaman arasında nasıl kimliğe bürünme gerçekleştirilip gerçekleştirilmediğine bakılmaksızın zaman uyumsuz noktalar, akışları olduğunu belirtir.|  
|[\<AppContextSwitchOverrides >](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|Tarafından kullanılan bir veya daha fazla anahtarları tanımlar <xref:System.AppContext> yeni işlevselliği için bir geri çevirme mekanizma sağlar sınıfını.|  
|[\<appDomainManagerAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|Varsayılan uygulama etki alanı işlemde uygulama etki alanı yöneticisi sağlayan derlemeyi belirtir.|  
|[\<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak görev yapan türünü belirtir.|  
|[\<appDomainResourceMonitoring >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|Ömür işlemin işlemdeki tüm uygulama etki alanlarında istatistikleri toplamak için çalışma zamanı bildirir.|  
|[\<assemblyBinding >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|  
|[\<bypassTrustedAppStrongNames >](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|Güvenilir derlemeler için tanımlayıcı ad doğrulaması atlanmasına olup olmadığını belirtir.|  
|[\<CompatSortNLSVersion >](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|Çalışma zamanı dize karşılaştırmaları yaparken eski sıralama davranışını kullanmalısınız belirtir.|  
|[\<developmentMode >](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|Çalışma zamanı derlemeleri DEVPATH ortam değişkeni tarafından belirtilen dizinleri arar olup olmadığını belirtir.|  
|[\<disableCachingBindingFailures >](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|Bağlama hataları .NET Framework sürüm 2. 0'de varsayılan davranışı olan önbelleğe almayı devre dışı bırakılıp bırakılmadığını belirtir.|  
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|Bir iş parçacığı başlatıldığında iş parçacığı yığınının tamamının taahhüt olup olmadığını belirtir.|  
|[\<disableFusionUpdatesFromADManager >](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|Uygulama etki alanı için yapılandırma ayarlarını geçersiz kılmak çalışma zamanı ana bilgisayarı izin vermek için varsayılan davranışı devre dışı bırakılıp bırakılmadığını belirtir.|  
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|Tarih ve saat yöntemleri ayrıştırma ayarlanmış bir kural kümesi yalnızca bir gün, ay, saat ve AM/PM göstergesi içeren tarih dizeleri ayrıştırılacak kullanıp kullanmadığını belirler.|  
|[\<Enforcefıpspolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|Şifreleme algoritmaları Federal Bilgi işleme standartları (FIPS ile) uyması gereken bir bilgisayar yapılandırma gereksinimini zorlanıp zorlanmayacağını belirtir.|  
|[\<etwEnable >](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|Olay İzleme (ETW) Windows için ortak dil çalışma zamanı olayları için etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads >](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|PerfCounter.dll CategoryOptions kayıt defteri ayarı bir .NET Framework sürüm 1.1 uygulamasında kategoriye özgü paylaşılan bellek ya da genel bellek performans sayacı verilerini yüklemek karar vermek için kullanıp kullanmayacağını belirtir.|  
|[\<gcAllowVeryLargeObjects >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|64-bit platformlarda toplam boyutu 2 gigabayttan (GB) büyük olan dizileri etkinleştirir.|  
|[\<gcConcurrent >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|Ortak dil çalışma zamanının atık toplama eşzamanlı olarak çalışıp çalışmayacağını belirtir.|  
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|Çöp toplama, birden fazla CPU grubu destekleyip desteklemediğini belirtir.|  
|[\<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|Ortak dil çalışma zamanı sunucu çöp toplama çalışıp çalışmayacağını belirtir.|  
|[\<generatePublisherEvidence >](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|Çalışma zamanı kod erişim güvenliği (CAS) Yayımcı ilkesi kullanıp kullanmayacağını belirtir.|  
|[\<legacyCorruptedStateExceptionsPolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|Erişim ihlalleri ve diğer bozuk durum özel durumları yakalamak yönetilen kod çalışma zamanı izin verip vermediğini belirtir.|  
|[\<Legacyımpersonationpolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Windows kimliği, geçerli iş parçacığı üzerindeki yürütme içeriği için akış ayarlarından bağımsız olarak zaman uyumsuz noktalar arasında geçmeyen belirtir.|  
|[\<loadfromRemoteSources >](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|Uzak kaynaktan derlemeleri tam güven yüklü olup olmadığını belirtir.|  
|[< NetFx40_LegacySecurityPolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|Çalışma zamanının eski kod erişimi güvenliği (CAS) ilkesi kullanıp kullanmayacağını belirtir.|  
|[< Netfx40_pınvokestackresilience >](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|Olup çalışma zamanı düzeltmeleri yanlış platform çağırma bildirimler arasında yavaş geçişler, çalışma zamanında otomatik olarak yönetilen ve yönetilmeyen kod belirtir.|  
|[< NetFx45_CultureAwareComparerGetHashCode_LongStrings >](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Çalışma zamanı için karma kodları hesaplamak üzere sabit miktarda bellek kullanıp kullanmayacağını belirtir <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi.|  
|[\<PreferComInsteadOfRemoting >](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|Çalışma zamanı uygulama etki alanı sınırları uzaktan iletişim yerine COM birlikte çalışma kullanacağını belirtir.|  
|[\<relativeBindForResources >](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|Araştırma için uydu derlemelerini en iyi duruma getirir.|  
|[\<shadowCopyVerifyByTimeStamp >](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|Gölge kopyalama sunulan varsayılan başlangıç davranışını kullanıp kullanmayacağını belirtir [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], veya .NET Framework'ün önceki sürümlerinde başlangıç davranışını geri döner.|  
|[\<supportPortability >](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|Bir uygulama derlemeleri uygulama taşınabilirliği amacıyla eşdeğer kabul eder varsayılan davranışı devre dışı bırakarak aynı derlemenin iki farklı uygulamalarında .NET Framework'ün başvurabileceğini belirtir.|  
|[\<System.Runtime.Caching >](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Varsayılan bellek içi nesne önbelleği için yapılandırma bilgileri sağlar.|  
|[<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtmadığını belirtir.|  
|[\<ThrowUnobservedTaskExceptions >](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|Çalışan bir işleme, işlenmemiş bir görev özel durumlarını sonlandırma olup olmadığını belirtir.|  
|[< TimeSpan_LegacyFormatMode >](../../../../../docs/framework/configure-apps/file-schema/runtime/timespan-legacyformatmode-element.md)|Çalışma zamanı için eski biçimlendirme kullanıp kullanmayacağını belirtir <xref:System.TimeSpan> değerleri.|  
|[\<useLegacyJit >](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|Ortak dil çalışma zamanı için tam zamanında derleme eski 64 bit JIT Derleyici kullanıp kullanmadığını belirler.|  
|[\<UseRandomizedStringHashAlgorithm >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|Çalışma zamanı için dizelerin karma kodlarını hesaplayıp belirtir bir her uygulama etki alanı.|  
|[\<Usesmallınternalthreadstacks >](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|İstekleri, belirli iş parçacıklarını oluşturduğunda, çalışma zamanı açık yığın boyutlarını kullanmak yerine varsayılan yığın boyutu dahili olarak kullanır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 Alt öğeleri [ \<çalışma zamanı >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) yapılandırma dosyasının bir uygulamanın nasıl yürüteceğini yapılandırmak için ortak dil çalışma zamanı tarafından kullanılır. Örneğin, [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) iş istasyonu çöp toplama veya sunucu çöp toplama, çöp toplayıcı kullanıp kullanmadığını belirler [ \< UseRandomizedStringHashAlgorithm >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md) ortak dil çalışma zamanı için bir uygulama başına veya bir uygulama başına etki alanı temelinde, dize karma kodlarını hesaplayıp belirler ve `AppContextSwitchOverrides` öğesi kitaplığı kullanıcıları sağlar. kabul et veya değiştirilen işlevler kitaplığı tarafından sağlanan dışında iyileştirilmiş için.  
  
 Öğeleri [ \<çalışma zamanı >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümü salt okunur otomatik olarak uygulama başlangıcında ortak dil çalışma zamanı tarafından. Varsayılan olmayan uygulama etki alanı için yapılandırma dosyası adının sağlanarak de tanımlayabilirsiniz <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> özelliği; uygulama etki alanı zaman yüklenir ayarlarına otomatik olarak okunur. Şimdiye kadar doğrudan ayarları okumak için bir gereksinim nadiren de olsa olmalıdır [ \<çalışma zamanı >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümüne uygulamanızın yapılandırma dosyasında.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
