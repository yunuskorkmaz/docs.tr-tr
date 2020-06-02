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
ms.openlocfilehash: 12dfdd3ac6d75a3e2a33f93d8847c963ded912e8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286099"
---
# <a name="application-domain-resource-monitoring"></a>Uygulama Etki Alanı Kaynak İzleme

Uygulama etki alanı kaynak izleme (ARM), ana bilgisayarların, uygulama etki alanı tarafından CPU ve bellek kullanımını izlemesini sağlar. Bu, uzun süre çalışan bir işlemde birçok uygulama etki alanı kullanan ASP.NET gibi konaklar için yararlıdır. Ana bilgisayar, tüm işlemin performansını olumsuz yönde etkileyen, ancak sorunlu uygulamayı belirleyebildiği bir uygulamanın uygulama etki alanını kaldırabilirler. ARM, bu tür kararlar verirken kullanılabilecek bilgiler sağlar.

Örneğin, bir barındırma hizmeti bir ASP.NET sunucusunda çalışan çok sayıda uygulamaya sahip olabilir. İşlemdeki bir uygulama çok fazla bellek veya çok fazla işlemci zamanı kullanmaya başlarsa, barındırma hizmeti, soruna neden olan uygulama etki alanını belirlemek için ARM 'yi kullanabilir.

ARM, canlı uygulamalarda kullanılmak üzere yeterince hafif. Windows için olay izleme (ETW) veya doğrudan yönetilen ya da yerel API 'Ler aracılığıyla bilgilere erişebilirsiniz.

## <a name="enabling-resource-monitoring"></a>Kaynak Izlemeyi etkinleştirme

ARM dört şekilde etkinleştirilebilir: ortak dil çalışma zamanı (CLR) başlatıldığında, yönetilmeyen bir barındırma API kullanarak, yönetilen kod kullanarak veya ARM ETW olaylarını dinleyerek, bir yapılandırma dosyası sağlayarak bir yapılandırma dosyası sağlayabilirsiniz.

ARM etkin hale geldiğinde, işlemdeki tüm uygulama etki alanlarında veri toplamaya başlar. ARM etkinleştirilmeden önce bir uygulama etki alanı oluşturulduysa, uygulama etki alanı oluşturulduğunda değil ARM etkinleştirildiğinde, toplu veriler başlar. Etkinleştirildikten sonra ARM devre dışı bırakılamaz.

- [\<appDomainResourceMonitoring>](../../framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)Yapılandırma dosyasına öğe ekleyerek ve özniteliğini olarak AYARLAYARAK clr BAŞLANGıCıNDA ARM `enabled` 'yi etkinleştirebilirsiniz `true` . `false`(Varsayılan) değeri, yalnızca ARM 'nin başlangıçta etkinleştirilmediği anlamına gelir; daha sonra diğer etkinleştirme mekanizmalarından birini kullanarak etkinleştirebilirsiniz.

- Konak, [ıclartppdomainresourcemonitor](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) barındırma ARABIRIMINI isteyerek ARM 'yi etkinleştirebilir. Bu arabirim başarılı bir şekilde alındıktan sonra ARM etkin olur.

- Yönetilen kod, statik ( `Shared` Visual Basic) özelliğini olarak AYARLAYARAK ARM 'yi etkinleştirebilir <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> `true` . Özelliği ayarlandığı anda ARM etkin olur.

- ETW olaylarını dinleyerek, başlangıçtan sonra ARM 'yi etkinleştirebilirsiniz. ARM etkin ve `Microsoft-Windows-DotNETRuntime` anahtar sözcüğünü kullanarak genel sağlayıcıyı etkinleştirdiğinizde tüm uygulama etki alanları için olayları sunmaya başlar `AppDomainResourceManagementKeyword` . Uygulama etki alanları ve iş parçacıkları ile verileri ilişkilendirmek için `Microsoft-Windows-DotNETRuntimeRundown` sağlayıcıyı anahtar sözcüğüyle de etkinleştirmeniz gerekir `ThreadingKeyword` .

## <a name="using-arm"></a>ARM kullanma

ARM, bir uygulama etki alanı tarafından kullanılan toplam işlemci süresini ve bellek kullanımı hakkında üç tür bilgiyi sağlar.

- **Bir uygulama etki alanı Için toplam işlemci süresi (saniye**): Bu, işletim sistemi tarafından, süresi boyunca uygulama etki alanında yürütmeyi geçen tüm iş parçacıkları için işletim sistemi tarafından bildirilen iş parçacığı süreleri eklenerek hesaplanır. Engellenen veya uyuyan iş parçacıkları işlemci zamanı kullanmaz. Bir iş parçacığı yerel koda çağırdığında, iş parçacığının yerel kodda harcadığı süre, Çağrının yapıldığı uygulama etki alanının sayımına dahil edilir.

  - Yönetilen API: <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> özelliği.

  - Barındırma API 'SI: [ıclartppdomainresourcemonitor:: GetCurrentCpuTime](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) yöntemi.

  - ETW olayları: `ThreadCreated` , `ThreadAppDomainEnter` ve `ThreadTerminated` olayları. Sağlayıcılar ve anahtar sözcükler hakkında daha fazla bilgi için bkz. [CLR ETW olaylarında](../../framework/performance/clr-etw-events.md)"AppDomain kaynak izleme olayları".

- **Bir uygulama etki alanı tarafından yaşam süresi boyunca, bayt cinsinden yapılan toplam yönetilen ayırma sayısı**: ayrılan nesneler kısa süreli olabileceğinden, toplam ayırma her zaman bir uygulama etki alanı tarafından bellek kullanımını yansıtmaz. Ancak, bir uygulama çok sayıda nesne ayırır ve serbest bırakır, ayırmaların maliyeti önemli olabilir.

  - Yönetilen API: <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> özelliği.

  - Barındırma API 'SI: [ıclartppdomainresourcemonitor:: Getcurrentalkonumlandırılan](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) yöntemi.

  - ETW olayları: `AppDomainMemAllocated` olay, `Allocated` alan.

- **Bir uygulama etki alanı tarafından başvurulan ve en son tam, engelleyici koleksiyonu kullanan, bayt cinsinden yönetilen bellek**: Bu sayı yalnızca tam, engelleyici bir koleksiyon sonrasında doğrudur. (Bu, arka planda gerçekleşen ve uygulamayı engellememe, eşzamanlı koleksiyonlara karşılık gelir.) Örneğin, <xref:System.GC.Collect?displayProperty=nameWithType> yöntem aşırı yüklemesi tam, engelleyici bir koleksiyon oluşmasına neden olur.

  - Yönetilen API: <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> özelliği.

  - Barındırma API 'SI: [ıclartppdomainresourcemonitor:: GetCurrentSurvived](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) yöntemi, `pAppDomainBytesSurvived` parametresi.

  - ETW olayları: `AppDomainMemSurvived` olay, `Survived` alan.

- **İşlem tarafından başvurulan ve en son tam ve engelleyici koleksiyonu kullanan toplam yönetilen bellek (bayt cinsinden**). ayrı uygulama etki alanları için kalan bellek bu sayıyla karşılaştırılabilir.

  - Yönetilen API: <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> özelliği.

  - Barındırma API 'SI: [ıclartppdomainresourcemonitor:: GetCurrentSurvived](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) yöntemi, `pTotalBytesSurvived` parametresi.

  - ETW olayları: `AppDomainMemSurvived` olay, `ProcessSurvived` alan.

### <a name="determining-when-a-full-blocking-collection-occurs"></a>Tam, engelleyici bir koleksiyonun ne zaman gerçekleşeceğini belirleme

Kalan bellek sayısının doğru olduğunu anlamak için, tam bir engelleme koleksiyonu ne zaman oluştuğunu bilmeniz gerekir. Bunu yapma yöntemi, ARM istatistiklerini incelemek için kullandığınız API 'ye bağlıdır.

#### <a name="managed-api"></a>Yönetilen API

Sınıfının özelliklerini kullanırsanız <xref:System.AppDomain> , <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> tam koleksiyonların bildirimine kaydolmak için yöntemini kullanabilirsiniz. Bir koleksiyonun yaklaşımı yerine bir koleksiyonun tamamlanmasını beklerken kullandığınız eşik önemli değildir. Daha sonra <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> , tam bir koleksiyon tamamlanana kadar engelleyen yöntemi çağırabilirsiniz. Bir döngüsünde yöntemi çağıran ve yöntemin her döndürdüğü her türlü gerekli Analizi yapan bir iş parçacığı oluşturabilirsiniz.

Alternatif olarak, <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> 2. nesil koleksiyonların sayısının arttığını görmek için yöntemini düzenli aralıklarla çağırabilirsiniz. Yoklama sıklığına bağlı olarak, bu teknik tam bir koleksiyonun oluşumunu doğru bir şekilde sağlamayabilir.

#### <a name="hosting-api"></a>Barındırma API 'SI

Yönetilmeyen barındırma API 'SI kullanırsanız, ana bilgisayarınız CLR 'yi [IHostGCManager](../../framework/unmanaged-api/hosting/ihostgcmanager-interface.md) arabiriminin bir uygulamasına iletmelidir. CLR, bir koleksiyon gerçekleştiğinde askıya alınmış iş parçacıklarının yürütülmesini sürdürürse, [IHostGCManager:: SuspensionEnding](../../framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) yöntemini çağırır. CLR, tamamlanmış koleksiyonun neslini metodun bir parametresi olarak geçirir, bu nedenle konak koleksiyonun tam veya kısmi olup olmadığını belirleyebilir. [IHostGCManager:: SuspensionEnding](../../framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) yöntemi uygulamanız, daha fazla bellek sorgulayabilir ve bu da sayımların güncelleştirildikten hemen sonra alındıklarından emin olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [ICLRAppDomainResourceMonitor Arabirimi](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [\<appDomainResourceMonitoring>](../../framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [CLR ETW Olayları](../../framework/performance/clr-etw-events.md)
