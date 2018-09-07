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
ms.openlocfilehash: 50d601d711579bce2e2651a1efc65d824a50d47a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44082104"
---
# <a name="application-domain-resource-monitoring"></a>Uygulama Etki Alanı Kaynak İzleme
Uygulama etki alanı kaynak izleme (ARM), uygulama etki alanı tarafından CPU ve bellek kullanımını izlemek için ana bilgisayarları etkinleştirir. Bu, ASP.NET gibi bir uzun süre çalışan işlemde birden çok uygulama etki alanı kullanan konaklar için kullanışlıdır. Konak, sorunlu uygulamayı tanımlayabilirsiniz, ancak tüm işlemin performansını olumsuz yönde etkileyen bir uygulamanın uygulama etki alanını boşaltma. ARM gibi kararları vermekte yardımcı olmak için kullanılabilecek bilgiler sağlar.  
  
 Örneğin, bir barındırma hizmeti bir ASP.NET sunucu üzerinde çalışan birçok uygulama olabilir. Çok fazla bellek veya çok fazla işlemci zamanı kullanan bir uygulamada bir işlem başlar, barındırma hizmeti ARM soruna neden olan uygulama etki alanını tanımlamak için kullanabilirsiniz.  
  
 ARM Canlı uygulamaları kullanmak için yeteri kadar basit. Olay izleme için Windows (ETW) veya yönetilen veya yerel API'ler aracılığıyla doğrudan kullanarak bilgilere erişebilir.  
  
## <a name="enabling-resource-monitoring"></a>Kaynak izlemeyi etkinleştirme  
 ARM dört şekilde etkinleştirilebilir: ortak dil çalışma zamanı (CLR) başlatıldığında bir yapılandırma dosyası sağlanarak, bir yönetilmeyen kullanarak yönetilen kod kullanarak veya ARM ETW olayları dinleme barındırma.  
  
 ARM etkin hemen ardından işlemdeki tüm uygulama etki alanlarında veri toplamaya başlar. Uygulama etki alanı, ARM etkinleştirmeden önce oluşturulduysa, ARM etkinleştirildiğinde olmayan uygulama etki alanı oluşturulurken toplu veriler başlatır. Etkinleştirildiğinde, ARM devre dışı bırakılamaz.  
  
-   CLR başlatma sırasında ARM ekleyerek etkinleştirebilirsiniz [ \<appDomainResourceMonitoring >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) yapılandırma dosyası ve ayarı öğesi `enabled` özniteliğini `true`. Değerini `false` ARM başlangıçta etkin değil (varsayılan) yalnızca anlamına gelir; bunu daha sonra bir etkinleştirme mekanizmalarını kullanarak etkinleştirebilirsiniz.  
  
-   Konak isteyerek ARM etkinleştirebilirsiniz [Iclrappdomainresourcemonitor](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) arabirimi barındırma. Bu arabirim başarıyla alındığında, ARM etkinleştirilir.  
  
-   Yönetilen kod, ARM statik ayarlayarak etkinleştirebilirsiniz (`Shared` Visual Basic'te) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> özelliğini `true`. ARM özelliği ayarlanmış hemen sonra etkinleştirilir.  
  
-   ETW olayları dinleyerek başlatma işleminden sonra ARM etkinleştirebilirsiniz. ARM etkindir ve genel sağlayıcısı etkinleştirdiğinizde, tüm uygulama etki alanları için olayları oluşturma başlar `Microsoft-Windows-DotNETRuntime` kullanarak `AppDomainResourceManagementKeyword` anahtar sözcüğü. Uygulama etki alanları ve iş parçacıkları ile verilerin bağıntısını kurmaya da etkinleştirmeniz gerekir `Microsoft-Windows-DotNETRuntimeRundown` sağlayıcısıyla `ThreadingKeyword` anahtar sözcüğü.  
  
## <a name="using-arm"></a>ARM kullanarak  
 ARM bir uygulama etki alanı ve bellek kullanımı hakkında bilgi üç tür tarafından kullanılan toplam işlemci zamanı sağlar.  
  
-   **Toplam uygulama etki alanı, işlemci süresini saniye cinsinden**: Bu uygulama etki alanında yaşam süresi boyunca yürütme süresi geçen tüm iş parçacıkları için işletim sistemi tarafından bildirilen iş parçacığı kez ekleyerek hesaplanır. Engellenen veya uykudaki iş parçacıkları, işlemci zamanı kullanmayın. Bir iş parçacığı yerel kod içine çağırdığında, yerel kodda iş parçacığı harcadığı zamanı sayısı Çağrının yapıldığı uygulama etki alanı için dahil edilir.  
  
    -   Yönetilen API: <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> özelliği.  
  
    -   API'sini barındıran: [Iclrappdomainresourcemonitor::getcurrentcputime](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) yöntemi.  
  
    -   ETW olayları: `ThreadCreated`, `ThreadAppDomainEnter`, ve `ThreadTerminated` olayları. Sağlayıcıları ve anahtar sözcükler hakkında daha fazla bilgi için bkz: "Uygulama etki alanı kaynak izleme olaylarını" [CLR ETW olaylarını](../../../docs/framework/performance/clr-etw-events.md).  
  
-   **Toplam bayt ömrü sırasında bir uygulama etki alanına göre yapılan yönetilen ayırmaların**: toplam miktar değil her zaman yansıtacak bir uygulama etki alanına göre bellek kullanımı ayrılan nesneler kısa süreli olabilir çünkü. Ancak, bir uygulama ayırır ve boşaltır büyük sayıda nesne içeren, ayırmaları maliyetini önemli olabilir.  
  
    -   Yönetilen API: <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> özelliği.  
  
    -   API'sini barındıran: [Iclrappdomainresourcemonitor::getcurrentallocated](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) yöntemi.  
  
    -   ETW olayları: `AppDomainMemAllocated` olay `Allocated` alan.  
  
-   **Yönetilen bir uygulama etki alanı tarafından başvurulur ve toplamayı engelleme en son tam kurtulan, bayt cinsinden bellek**: Bu sayı bir tam sonra yalnızca koleksiyon engelleme doğrudur. (Arka planda gerçekleşir ve uygulama engelleme eş zamanlı koleksiyonlar aksine budur.) Örneğin, <xref:System.GC.Collect?displayProperty=nameWithType> yöntemi aşırı yüklemesi, tam toplamayı engelleme, neden olur.  
  
    -   Yönetilen API: <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> özelliği.  
  
    -   API'sini barındıran: [Iclrappdomainresourcemonitor::getcurrentsurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) yöntemi `pAppDomainBytesSurvived` parametresi.  
  
    -   ETW olayları: `AppDomainMemSurvived` olay `Survived` alan.  
  
-   **Toplam işlem tarafından başvurulan ve toplamayı engelleme en son tam kurtulan yönetilen, bayt cinsinden bellek**: her bir uygulama etki alanları için kalan bellek bu sayının için karşılaştırılabilir.  
  
    -   Yönetilen API: <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> özelliği.  
  
    -   API'sini barındıran: [Iclrappdomainresourcemonitor::getcurrentsurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) yöntemi `pTotalBytesSurvived` parametresi.  
  
    -   ETW olayları: `AppDomainMemSurvived` olay `ProcessSurvived` alan.  
  
### <a name="determining-when-a-full-blocking-collection-occurs"></a>Tam olduğunda belirleme, toplamayı engelleme gerçekleşir  
 Kalan bellek sayısı doğru olduğunda belirlemek için tam ve engelleyici bir koleksiyon yalnızca zaman oluştu bilmeniz gerekir. Bunu yapmak için yöntem ARM istatistikleri incelemek için kullandığınız API'ye bağlıdır.  
  
#### <a name="managed-api"></a>Yönetilen API  
 Özelliklerini kullanıyorsanız <xref:System.AppDomain> kullanabileceğiniz sınıfı <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> bildirimi tam bir koleksiyon için yöntemi. Bir koleksiyonun yaklaşım yerine tamamlandığında, bir koleksiyon için bekleyen çünkü kullandığınız eşiği önemli değildir. Ardından çağırabilirsiniz <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> tam bir koleksiyon tamamlanıncaya kadar engeller yöntemi. Yöntemi döndürür. her gerekli herhangi bir analiz yapar ve bir döngüde yöntemi çağıran bir iş parçacığı oluşturabilirsiniz.  
  
 Alternatif olarak, çağırabilirsiniz <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> düzenli aralıklarla 2. nesil koleksiyonlar sayısı arttı görmek için yöntemi. Yoklama sıklığı bağlı olarak, bu teknik olarak doğru bir göstergesi tam bir koleksiyon oluşumunu sağlamayabilir.  
  
#### <a name="hosting-api"></a>Barındırma API'si  
 Yönetilmeyen barındırma API'SİNİN kullanıyorsanız, ana CLR uygulaması geçmelidir [Ihostgcmanager](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) arabirimi. CLR çağrıları [Ihostgcmanager::suspensionending](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) yöntemi bir koleksiyon gerçekleşirken, askıya alınmış iş parçacıklarının yürütülmesini sürdürür. Konak koleksiyonu tam veya kısmi olup olmadığını belirlemek için CLR tamamlanmış koleksiyon oluşturma yönteminin bir parametresi olarak geçirir. Uygulamanıza [Ihostgcmanager::suspensionending](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) yöntemi güncelleştirmeden hemen sonra sayıları alındığından emin olmak için kalan bellek için sorgulayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
- [ICLRAppDomainResourceMonitor Arabirimi](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
- [\<appDomainResourceMonitoring >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
- [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
