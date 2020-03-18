---
title: Uygulama Etki Alanı Kaynak İzleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- monitoring managed memory use by application domain
- application domains, memory use
- memory use, monitoring
- application domains, resource monitoring
ms.assetid: 318bedf8-7f35-4f00-b34a-2b7b8e3fa315
ms.openlocfilehash: 54e300bef1818fd08f27d7920eec68ee1f2c45bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141388"
---
# <a name="application-domain-resource-monitoring"></a>Uygulama Etki Alanı Kaynak İzleme

Uygulama etki alanı kaynak izleme (ARM) ana bilgisayarların uygulama etki alanı tarafından CPU ve bellek kullanımını izlemek için olanak sağlar. Bu, uzun süren bir işlemde çok sayıda uygulama etki alanı kullanan ASP.NET gibi ana bilgisayarlar için yararlıdır. Ana bilgisayar, tüm işlemin performansını olumsuz etkileyen bir uygulamanın uygulama etki alanını, ancak sorunlu uygulamayı tanımlayabiliyorsa boşaltabilir. ARM, bu tür kararların alınmasına yardımcı olmak için kullanılabilecek bilgiler sağlar.

Örneğin, bir barındırma hizmetinin ASP.NET bir sunucuda çalışan birçok uygulaması olabilir. İşlemdeki bir uygulama çok fazla bellek veya çok fazla işlemci süresi tüketmeye başlarsa, barındırma hizmeti soruna neden olan uygulama etki alanını tanımlamak için ARM'yi kullanabilir.

ARM canlı uygulamalarda kullanmak için yeterince hafiftir. Bilgilere Windows için olay izleme (ETW) kullanarak veya doğrudan yönetilen veya yerel API'ler aracılığıyla erişebilirsiniz.

## <a name="enabling-resource-monitoring"></a>Kaynak İzlemeyi Etkinleştirme

ARM dört şekilde etkinleştirilebilir: ortak dil çalışma zamanı (CLR) başlatıldığında bir yapılandırma dosyası sağlayarak, yönetilmeyen bir barındırma API'si kullanarak, yönetilen kodu kullanarak veya ARM ETW olaylarını dinleyerek.

ARM etkinleştirilir etkinleştirmez, işlemdeki tüm uygulama etki alanlarında veri toplamaya başlar. ARM etkinleştirilmeden önce bir uygulama etki alanı oluşturulduysa, tamamlayınca veri ARM etkinleştirildiğinde başlar, uygulama etki alanı oluşturulduğunda değil. Etkinleştirildikten sonra ARM devre dışı tutulamaz.

- ClR'de ARM'ı yapılandırma dosyasına `enabled` `true` [ \<appDomainResourceMonitoring>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) öğesini ekleyerek ve özniteliği ayarlayarak etkinleştirebilirsiniz. `false` (Varsayılan) değeri, yalnızca ARM'ın başlangıçta etkinleştirilmediğini anlamına gelir; daha sonra diğer etkinleştirme mekanizmalarından birini kullanarak etkinleştirebilirsiniz.

- Ev sahibi [ICLRAppDomainResourceMonitor](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) barındırma arabirimini isteyerek ARM'ı etkinleştirebilir. Bu arabirim başarıyla elde edildikten sonra ARM etkinleştirilir.

- Yönetilen kod, statik (Visual`Shared` Basic'te) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> özelliğini . `true` Özellik ayarlanır ayarlanmaz ARM etkinleştirilir.

- ETW olaylarını dinleyerek başlangıç tan sonra ARM'ı etkinleştirebilirsiniz. ARM etkindir ve anahtar sözcüğü kullanarak ortak sağlayıcıyı `Microsoft-Windows-DotNETRuntime` etkinleştirdiğinizde `AppDomainResourceManagementKeyword` tüm uygulama etki alanları için olayları yükseltmeye başlar. Verileri uygulama etki alanları ve iş parçacıklarıyla ilişkilendirmek `Microsoft-Windows-DotNETRuntimeRundown` için, `ThreadingKeyword` sağlayıcıyı anahtar kelimeyle etkinleştirmeniz gerekir.

## <a name="using-arm"></a>ARM kullanma

ARM, bir uygulama etki alanı tarafından kullanılan toplam işlemci süresini ve bellek kullanımı yla ilgili üç tür bilgi sağlar.

- **Bir uygulama etki alanı için toplam işlemci süresi, saniye cinsinden**: Bu, kullanım süresi boyunca uygulama etki alanında yürütülerek zaman harcayan tüm iş parçacıkları için işletim sistemi tarafından bildirilen iş parçacığı süreleri eklenerek hesaplanır. Engellenen veya uyku iş parçacığı işlemci süresini kullanmaz. Bir iş parçacığı yerel koda çağrı yaptığında, iş parçacığının yerel kodda harcadığı süre, aramanın yapıldığı uygulama etki alanının sayısına dahil edilir.

  - Yönetilen API: <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> özellik.

  - Hosting API: [ICLRAppDomainResourceMonitor::GetCurrentCpuTime](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) yöntemi.

  - ETW `ThreadCreated`olaylar: `ThreadAppDomainEnter`, `ThreadTerminated` , ve olaylar. Sağlayıcılar ve anahtar kelimeler hakkında daha fazla bilgi için [CLR ETW Etkinlikleri'ndeki](../../../docs/framework/performance/clr-etw-events.md)"AppDomain Kaynak İzleme Etkinlikleri"ne bakın.

- **Bir uygulama etki alanı tarafından kullanım ömrü boyunca, baytolarak yapılan toplam yönetilen ayırmalar**: Ayrılan nesneler kısa ömürlü olabileceğinden, toplam ayırmalar her zaman bir uygulama etki alanı tarafından bellek kullanımını yansıtmaz. Ancak, bir uygulama çok sayıda nesne ayırır ve serbest kalırsa, ayırmamaliyeti önemli olabilir.

  - Yönetilen API: <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> özellik.

  - Hosting API: [ICLRAppDomainResourceMonitor::GetCurrentAllocated](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) yöntemi.

  - ETW olaylar: `AppDomainMemAllocated` `Allocated` olay, alan.

- **Yönetilen bellek, bayt, bir uygulama etki alanı tarafından başvurulan ve en son tam hayatta, engelleme toplama**: Bu sayı sadece tam, engelleme toplama sonra doğrudur. (Bu, arka planda oluşan ve uygulamayı engellemeyen eşzamanlı koleksiyonlarla tezat oluşturuyor.) Örneğin, <xref:System.GC.Collect?displayProperty=nameWithType> yöntem aşırı yükleme tam, engelleme toplama neden olur.

  - Yönetilen API: <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> özellik.

  - Hosting API: [ICLRAppDomainResourceMonitor::GetCurrentSurvive](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) yöntemi, `pAppDomainBytesSurvived` parametre.

  - ETW olaylar: `AppDomainMemSurvived` `Survived` olay, alan.

- **Toplam yönetilen bellek, bayt, bu işlem tarafından başvurulan ve en son tam hayatta, engelleme toplama**: Tek tek uygulama etki alanları için hayatta bellek bu sayı ile karşılaştırılabilir.

  - Yönetilen API: <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> özellik.

  - Hosting API: [ICLRAppDomainResourceMonitor::GetCurrentSurvive](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) yöntemi, `pTotalBytesSurvived` parametre.

  - ETW olaylar: `AppDomainMemSurvived` `ProcessSurvived` olay, alan.

### <a name="determining-when-a-full-blocking-collection-occurs"></a>Tam, Engelleme Koleksiyonu'nun Ne Zaman Oluştuğunu Belirleme

Hayatta kalan bellek sayılarının ne zaman doğru olduğunu belirlemek için, tam, engelleme koleksiyonunun ne zaman oluştuğunu bilmeniz gerekir. Bunu yapmak için yöntem ARM istatistiklerini incelemek için kullandığınız API bağlıdır.

#### <a name="managed-api"></a>Yönetilen API

<xref:System.AppDomain> Sınıfın özelliklerini kullanıyorsanız, tam koleksiyonların <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> bildirimi için kayıt için yöntemi kullanabilirsiniz. Bir koleksiyonun yaklaşımıyerine bir koleksiyonun tamamlanmasını beklediğiniz için kullandığınız eşik önemli değildir. Daha sonra, <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> tam bir koleksiyon tamamlanana kadar engelleyen yöntemi arayabilirsiniz. Yöntemi döngü içinde çağıran ve yöntem döndüğünde gerekli tüm çözümlemesi yapan bir iş parçacığı oluşturabilirsiniz.

Alternatif olarak, nesil <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> 2 koleksiyonlarının sayısının artıp artmadığını görmek için yöntemi düzenli aralıklarla arayabilirsiniz. Yoklama sıklığına bağlı olarak, bu teknik tam bir koleksiyonun oluşumunun doğru bir göstergesi olarak sağlamayabilir.

#### <a name="hosting-api"></a>Hosting API

Yönetilmeyen barındırma API'sini kullanıyorsanız, ana bilgisayarınızın [CLR'den IHostGCManager](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) arabiriminin bir uygulamasını geçmesi gerekir. CLR, bir koleksiyon oluşurken askıya alınan iş parçacıklarının yürütülmesine devam ettiğinde [IHostGCManager::SuspensionEnding](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) yöntemini çağırır. CLR, tamamlanan koleksiyonun oluşturmasını yöntemin bir parametresi olarak geçirir, böylece ana bilgisayar koleksiyonun tam veya kısmi olup olmadığını belirleyebilir. [IHostGCManager uygulamanız::SuspensionEnding](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) yöntemi, sayımların güncelleştirilir güncellenmez alınmasını sağlamak için hayatta kalan bellek için sorgulayabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [ICLRAppDomainResourceMonitor Arabirimi](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [\<appDomainResourceMonitoring>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
