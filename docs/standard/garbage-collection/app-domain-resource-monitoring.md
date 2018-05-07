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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45b0f8293b41d42114b189c3ebe917a4f64c4f27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="application-domain-resource-monitoring"></a>Uygulama Etki Alanı Kaynak İzleme
Uygulama etki alanı kaynak izleme (ARM) uygulama etki alanı tarafından CPU ve bellek kullanımını izlemek ana bilgisayarları sağlar. Bu, ASP.NET gibi bir uzun süre çalışan işlemde birden çok uygulama etki alanı kullanan konakları için kullanışlıdır. Ana bilgisayar sorunlu uygulamayı belirleyebiliyorsanız, ancak yalnızca bütün işlem performansını olumsuz yönde etkileyen bir uygulamanın uygulama etki alanını boşaltma. ARM böyle kararları vermekte yol yardımcı olmak için kullanılan bilgileri sağlar.  
  
 Örneğin, bir barındırma hizmeti bir ASP.NET sunucu üzerinde çalışan birçok uygulama olabilir. Çok fazla bellek veya çok fazla işlemci zamanı kullanan bir uygulama işleminde başlıyorsa, barındırma hizmeti ARM soruna neden olan uygulama etki alanını tanımlamak için kullanabilirsiniz.  
  
 Canlı uygulamalarında kullanmak için yeterince basit koludur. Olay izleme için Windows (ETW) veya yönetilen veya özgün API'leri aracılığıyla doğrudan kullanarak bilgilere erişebilir.  
  
## <a name="enabling-resource-monitoring"></a>Kaynak izlemeyi etkinleştirme  
 ARM dört şekilde etkinleştirilebilir: ortak dil çalışma zamanı (CLR) başlatıldığında bir yapılandırma dosyası sağlayarak, yönetilmeyen kullanarak API, yönetilen kod kullanarak veya ARM ETW olayları dinleme barındırma.  
  
 ARM etkin olarak işlemdeki tüm uygulama etki alanları veri toplamaya başlar. Uygulama etki alanı ARM etkinleştirilmeden önce oluşturulduysa olmayan uygulama etki alanı oluşturulduğunda ARM etkin olduğunda toplu veri başlatır. Etkinleştirildiğinde, ARM devre dışı bırakılamaz.  
  
-   Ekleyerek CLR başlangıçta ARM etkinleştirebilirsiniz [ \<appDomainResourceMonitoring >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) yapılandırma dosyasını ve ayarı öğesine `enabled` özniteliğini `true`. Değerini `false` ARM başlangıçta etkin değil (varsayılan) yalnızca anlamına gelir; daha sonra bir etkinleştirme mekanizmaları birini kullanarak etkinleştirebilirsiniz.  
  
-   Ana bilgisayar isteyerek ARM etkinleştirebilirsiniz [Iclrappdomainresourcemonitor](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) arabirimi barındırma. Bu arabirim başarıyla alındığında, ARM etkinleştirilir.  
  
-   Yönetilen kod, ARM statik ayarlayarak etkinleştirebilir (`Shared` Visual Basic'te) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> özelliğine `true`. Özellik ayarlanmışsa hemen ARM etkinleştirilir.  
  
-   ETW olayları dinleyerek başlatma işleminden sonra ARM etkinleştirebilirsiniz. ARM etkinleştirilir ve ortak sağlayıcısı etkinleştirdiğinizde, tüm uygulama etki alanları için olaylar oluşturma başlar `Microsoft-Windows-DotNETRuntime` kullanarak `AppDomainResourceManagementKeyword` anahtar sözcüğü. Uygulama etki alanları ve iş parçacığı ile verilerin bağıntısını kurmaya da etkinleştirmeniz gerekir `Microsoft-Windows-DotNETRuntimeRundown` sağlayıcısıyla `ThreadingKeyword` anahtar sözcüğü.  
  
## <a name="using-arm"></a>ARM kullanma  
 ARM uygulama etki alanı ve bellek kullanımı hakkında bilgi üç tür tarafından kullanılan toplam işlemci süresi sağlar.  
  
-   **Bir uygulama etki alanı için işlemci süresini saniye cinsinden toplam**: Bu uygulama etki alanında yaşam süresi boyunca yürütme süresi geçen tüm iş parçacıklarının işletim sistemi tarafından bildirilen iş parçacığı kez ekleyerek hesaplanır. Engellenen veya Uyuyan iş parçacığı işlemci zamanı kullanmayın. Bir iş parçacığı yerel kod içine aradığında, yerel kodda iş parçacığı harcadığı zamanı çağrı yapıldığı uygulama etki alanı için sayısı dahil edilir.  
  
    -   Yönetilen API: <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> özelliği.  
  
    -   API barındırma: [Iclrappdomainresourcemonitor::getcurrentcputime](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) yöntemi.  
  
    -   ETW olayları: `ThreadCreated`, `ThreadAppDomainEnter`, ve `ThreadTerminated` olaylar. Sağlayıcıları ve anahtar sözcükler hakkında daha fazla bilgi için bkz: "Uygulama etki alanı kaynak izleme olayları" [CLR ETW olayları](../../../docs/framework/performance/clr-etw-events.md).  
  
-   **Toplam bayt ömrü sırasında bir uygulama etki alanı tarafından yapılan yönetilen ayırmaları**: toplam ayırmaları değil her zaman yansıtacak bir uygulama etki alanı tarafından bellek kullanımını ayrılmış nesneler kısa süreli olabilir çünkü. Ancak, bir uygulama ayırır ve büyük sayıda nesnelerin boşaltır, ayırmaları maliyetini önemli olabilir.  
  
    -   Yönetilen API: <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> özelliği.  
  
    -   API barındırma: [Iclrappdomainresourcemonitor::getcurrentallocated](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) yöntemi.  
  
    -   ETW olayları: `AppDomainMemAllocated` olayı `Allocated` alan.  
  
-   **Yönetilen bir uygulama etki alanı tarafından başvurulan ve koleksiyon engelleme en son tam derdi bitti bellek, bayt cinsinden**: Bu numarayı yalnızca tam sonra koleksiyon engelleme doğrudur. (Arka planda oluşur ve uygulamayı engellemez eşzamanlı koleksiyonları aksine budur.) Örneğin, <xref:System.GC.Collect?displayProperty=nameWithType> yöntemi aşırı yüklemesini koleksiyon engelleme tam, neden olur.  
  
    -   Yönetilen API: <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> özelliği.  
  
    -   API barındırma: [Iclrappdomainresourcemonitor::getcurrentsurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) yöntemi, `pAppDomainBytesSurvived` parametresi.  
  
    -   ETW olayları: `AppDomainMemSurvived` olayı `Survived` alan.  
  
-   **Toplam işlem tarafından başvurulan ve koleksiyon engelleme en son tam derdi bitti yönetilen bellek, bayt cinsinden**: survived bellek tek tek uygulama etki alanları için bu sayıya karşılaştırılabilir.  
  
    -   Yönetilen API: <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> özelliği.  
  
    -   API barındırma: [Iclrappdomainresourcemonitor::getcurrentsurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) yöntemi, `pTotalBytesSurvived` parametresi.  
  
    -   ETW olayları: `AppDomainMemSurvived` olayı `ProcessSurvived` alan.  
  
### <a name="determining-when-a-full-blocking-collection-occurs"></a>Tam olduğunda belirleme, koleksiyon engelleme oluşur  
 Bellek derdi bitti sayıları doğru olduğunda belirlemek için tam, engelleme koleksiyonu yalnızca ne zaman oluştu bilmeniz gerekir. Bunu yapmak için kullanılan yöntem ARM istatistikleri incelemek için kullandığınız API'ye bağlıdır.  
  
#### <a name="managed-api"></a>Yönetilen API  
 Özelliklerini kullanıyorsanız <xref:System.AppDomain> kullanabileceğiniz sınıfı, <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> tam koleksiyonları bildirimi için kaydolmaya yöntemi. Bir koleksiyon yaklaşımı yerine tamamlandığında, bir koleksiyon için bekleyen için kullandığınız eşik önemli değil. Ardından çağırabilirsiniz <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> tam bir koleksiyon tamamlanana kadar engeller yöntemi. Bir döngüde yöntemini çağırır ve yöntem döndürür her tüm gerekli analiz etmez bir iş parçacığı oluşturabilirsiniz.  
  
 Alternatif olarak, çağırabilirsiniz <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> 2. nesil koleksiyon sayısı arttıkça, düzenli aralıklarla görmek için yöntem. Yoklama sıklığı bağlı olarak, bu teknik olarak doğru bir göstergesi tam bir koleksiyon oluşum sağlamayabilir.  
  
#### <a name="hosting-api"></a>API barındırma  
 Yönetilmeyen barındırma API kullanırsanız, ana bilgisayar uygulaması CLR geçmesi [Ihostgcmanager](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) arabirimi. CLR çağrıları [Ihostgcmanager::suspensionending](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) koleksiyonu gerçekleşirken askıya alınan iş parçacığı yürütme devam ettiğinde yöntemi. Konak koleksiyonu tam veya kısmi olup olmadığını belirlemek için CLR tamamlanmış koleksiyonu oluşturma yönteminin parametre olarak geçirir. Uygulamanıza [Ihostgcmanager::suspensionending](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) yöntemi güncelleştirilmeden hemen sayımları alındığından emin olmak için derdi bitti belleğin, sorgulayabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [ICLRAppDomainResourceMonitor Arabirimi](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [\<appDomainResourceMonitoring >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
