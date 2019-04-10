---
title: CLR ETW Sağlayıcılar
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 639ebe1552fd3950bd77acd7b5730b0d3bdb150f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302627"
---
# <a name="clr-etw-providers"></a><span data-ttu-id="6c3a0-102">CLR ETW Sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="6c3a0-102">CLR ETW Providers</span></span>
<span data-ttu-id="6c3a0-103">Ortak dil çalışma zamanı (CLR) iki sağlayıcıları vardır: çalışma zamanı sağlayıcısı ve Özet sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-103">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="6c3a0-104">Çalışma zamanı sağlayıcısı olayları, etkin anahtar sözcüklere (olayların kategorilerini) bağlı olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-104">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="6c3a0-105">Örneğin, etkinleştirerek yükleyici olaylarını toplayan `LoaderKeyword` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-105">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="6c3a0-106">Olay izleme için Windows (ETW) olayları, daha sonra gerektiğinde virgülle ayrılmış değer (.csv) dosyalarında sonrası işlenebilecek bir .etl uzantılı bir dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-106">Event tracking for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="6c3a0-107">.Etl dosyasını bir .csv dosyasına dönüştürme hakkında daha fazla bilgi için bkz: [denetleme .NET Framework günlük](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="6c3a0-107">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="6c3a0-108">Çalışma zamanı sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="6c3a0-108">The Runtime Provider</span></span>  
 <span data-ttu-id="6c3a0-109">Çalışma zamanı sağlayıcısı ana CLR ETW sağlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-109">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="6c3a0-110">CLR çalışma zamanı sağlayıcısı GUID e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-110">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="6c3a0-111">Oturum ve yaygın olarak kullanılabilen araçları kullanarak CLR ETW olaylarını görüntülemek örnekleri için bkz. [denetleme .NET Framework günlük](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="6c3a0-111">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
 <span data-ttu-id="6c3a0-112">Anahtar sözcükler gibi kullanmanın yanı sıra `LoaderKeyword`, çok sık harekete olaylar günlüğe anahtar sözcükleri etkinleştirmek zorunda kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-112">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="6c3a0-113">`StartEnumerationKeyword` Ve `EndEnumerationKeyword` anahtar sözcükleri bu olayları etkinleştirmektedir ve de özetlenmiştir [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6c3a0-113">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="6c3a0-114">Özet sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="6c3a0-114">The Rundown Provider</span></span>  
 <span data-ttu-id="6c3a0-115">Özet sağlayıcısı bazı özel amaçlı kullanımlar için açık olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-115">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="6c3a0-116">Ancak, kullanıcıların çoğu için çalışma zamanı sağlayıcısı yeterli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-116">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="6c3a0-117">CLR özeti sağlayıcısının GUID A669021C-C450-4609-A035-5AF59AF4DF18 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-117">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="6c3a0-118">Normalde, önce bir işlem başlatır ve süreç bittikten sonra günlük kaydı kapalı ETW günlük kaydı etkindir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-118">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="6c3a0-119">Ancak, işlem yürütülürken ETW günlük kaydı açıksa, işlemleri hakkında ek bilgi gerekmiyor.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-119">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="6c3a0-120">Örneğin, sembol çözümleme için günlük açılmadan önce zaten yüklenmiş olan yöntemler için yöntem olaylarının günlüğe gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-120">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="6c3a0-121">`DCStart` Ve `DCEnd` olayları kaydetme işleminin durumunu veri toplama başlatıldığında ve durduruldu.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-121">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="6c3a0-122">(Durum zaten tam derlenmiş zamanında (JIT) yöntemleri ve yüklenmiş derlemeler de dahil olmak üzere, yüksek bir düzeyde bilgi ifade eder.) Bu iki olay süreçte çoktan olmuş hakkında bilgi sağlayabilir. Örneğin, hangi yöntemlerin JIT-derlenmiş ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-122">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="6c3a0-123">Sadece olaylar `DC`, `DCStart`, `DCEnd`, veya `DCInit` adları içinde Özet sağlayıcı altında üretilir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-123">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="6c3a0-124">Ayrıca, bu olaylar yalnızca Özet sağlayıcı altında üretilir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-124">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="6c3a0-125">Olay anahtar sözcük filtrelerine ek olarak, Özet sağlayıcı da destekler `StartRundownKeyword` ve `EndRundownKeyword` sağlamak için anahtar sözcükler hedeflenen filtreleme.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-125">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="6c3a0-126">Özeti Başlat</span><span class="sxs-lookup"><span data-stu-id="6c3a0-126">Start Rundown</span></span>  
 <span data-ttu-id="6c3a0-127">Özet sağlayıcı altındaki günlük ile etkinleştirilince başlangıç özeti tetiklenir `StartRundownKeyword` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-127">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="6c3a0-128">Bu neden `DCStart` oluşturulması için olay ve sistemin durumunu yakalar.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-128">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="6c3a0-129">Numaralandırma başlamadan önce `DCStartInit` olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-129">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="6c3a0-130">Numaralandırmanın sonunda `DCStartComplete` veri toplama normal şekilde sona ermesinin olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-130">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="6c3a0-131">Özet sonu</span><span class="sxs-lookup"><span data-stu-id="6c3a0-131">End Rundown</span></span>  
 <span data-ttu-id="6c3a0-132">Özet sonu, Özet sağlayıcı altındaki günlük ile etkin olduğunda tetiklenir `EndRundownKeyword` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-132">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="6c3a0-133">Yürütülecek devam eden süreçte profil oluşturmayı son Özet durdurur.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-133">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="6c3a0-134">`DCEnd` Olayları, profil oluşturma durduğunda sistem durumunu yakalar.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-134">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="6c3a0-135">Numaralandırma başlamadan önce `DCEndInit` olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-135">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="6c3a0-136">Numaralandırmanın sonunda `DCEndComplete` olayı, veri toplama olağan biçimde sona ermesini tüketiciye bildirmek üzere oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-136">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="6c3a0-137">Özeti başlatma ve sonu temelde sembol çözümlemesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-137">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="6c3a0-138">Başlangıç özeti profil oluşturma oturumu başlatılmasından önce önceden derlenmiş JIT yöntemleri için adres aralığı bilgisi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-138">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="6c3a0-139">Özet sonu profil oluşturma hakkında devre dışı olacağı sırada, JIT olarak derlenmiş tüm yöntemleri için adres aralığı bilgisi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-139">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="6c3a0-140">Profil oluşturma oturumu durdurulduğunda Özet sonu otomatik olarak gerçekleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-140">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="6c3a0-141">Bunun yerine, CLR özeti sağlayıcısı oturumunu ile açıkça çağırmak sembol isteyen bir araç olan `EndRundownKeyword` yalnızca profil oluşturma durdurulmadan önce etkin anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-141">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="6c3a0-142">Yönetilen sembol çözme yöntemi adres aralığı bilgisi başlangıç özeti veya Sonlandır özeti sağlamasına karşın, kullanmanızı öneririz `EndRundownKeyword` anahtar sözcüğü (kaynak olan `DCEnd` olayları) yerine `StartRundownKeyword` anahtar sözcüğü (Bu Kaynakları `DCStart` olayları).</span><span class="sxs-lookup"><span data-stu-id="6c3a0-142">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="6c3a0-143">Kullanarak `StartRundownKeyword` özeti profil oluşturulan senaryoyu bozabilir profil oluşturma oturumu sırasında oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-143">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="6c3a0-144">Çalışma zamanı ve Özet sağlayıcılarını kullanarak ETW veri toplama</span><span class="sxs-lookup"><span data-stu-id="6c3a0-144">ETW Data Collection Using Runtime and Rundown Providers</span></span>  
 <span data-ttu-id="6c3a0-145">Aşağıdaki örnek CLR özeti sağlayıcısının sembol çözümleme işlemlerini başlatmak veya profil penceresinin içinde veya dışında son bağımsız olarak en az etki ile yönetilen işlemlerin izin veren bir şekilde kullanmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-145">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1. <span data-ttu-id="6c3a0-146">CLR çalışma zamanı sağlayıcısını kullanarak ETW günlüğünü açın:</span><span class="sxs-lookup"><span data-stu-id="6c3a0-146">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     <span data-ttu-id="6c3a0-147">Günlük clr1.etl dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-147">The log will be saved to the clr1.etl file.</span></span>  
  
2. <span data-ttu-id="6c3a0-148">Yürütülecek işlem devam ederken profil oluşturmayı durdurmak için yakalamak için Özet sağlayıcı Başlat `DCEnd` olayları:</span><span class="sxs-lookup"><span data-stu-id="6c3a0-148">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     <span data-ttu-id="6c3a0-149">Bu topluluğunun `DCEnd` Özet oturumu başlatmak için olayları.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-149">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="6c3a0-150">Tüm olayların toplanması için 30 ila 60 saniye beklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-150">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="6c3a0-151">Günlük clr1.et2 dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-151">The log will be saved to the clr1.et2 file.</span></span>  
  
3. <span data-ttu-id="6c3a0-152">Tüm ETW profil oluşturmalarını devre dışı bırakın:</span><span class="sxs-lookup"><span data-stu-id="6c3a0-152">Turn off all ETW profiling:</span></span>  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4. <span data-ttu-id="6c3a0-153">Tek bir günlük dosyası oluşturmak üzere profilleri birleştirme:</span><span class="sxs-lookup"><span data-stu-id="6c3a0-153">Merge the profiles to create one log file:</span></span>  
  
    ```  
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="6c3a0-154">Merged.etl dosyası çalışma zamanı ve özeti sağlayıcısı oturumlarından gelen olayları içerir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-154">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="6c3a0-155">Adım 2 ve 3 (bir Özet oturumunun başlatılması ve ardından profil oluşturma sonlandırma) hemen bir kullanıcı profili oluşturma devre dışı kapatmak yerine bir aracı yürütebilir durdurulması için profil oluşturma isteği.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-155">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="6c3a0-156">Bir aracı, 4. adım olarak ayrıca yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-156">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c3a0-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c3a0-157">See also</span></span>

- [<span data-ttu-id="6c3a0-158">Ortak Dil Çalışma Zamanında ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="6c3a0-158">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
