---
title: CLR ETW Sağlayıcılar
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec83bfd08277c79f15904d50a85e43cc61ecd527
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894704"
---
# <a name="clr-etw-providers"></a><span data-ttu-id="54cf2-102">CLR ETW Sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="54cf2-102">CLR ETW Providers</span></span>
<span data-ttu-id="54cf2-103">Ortak dil çalışma zamanı (CLR) iki sağlayıcıya sahiptir: çalışma zamanı sağlayıcısı ve runaşağı sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="54cf2-103">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="54cf2-104">Çalışma zamanı sağlayıcısı, hangi anahtar sözcüklere (olay kategorileri) etkin olarak olaylar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54cf2-104">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="54cf2-105">Örneğin, `LoaderKeyword` anahtar sözcüğünü etkinleştirerek yükleyici olaylarını toplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54cf2-105">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="54cf2-106">Windows için olay Izleme (ETW) olayları, daha sonra gerektiğinde virgülle ayrılmış değer (. csv) dosyalarında işlenmek üzere bir. etl uzantısı olan bir dosyada günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-106">Event Tracing for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="54cf2-107">. Etl dosyasını. csv dosyasına dönüştürme hakkında daha fazla bilgi için bkz. [.NET Framework günlüğünü denetleme](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="54cf2-107">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="54cf2-108">Çalışma zamanı sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="54cf2-108">The Runtime Provider</span></span>  
 <span data-ttu-id="54cf2-109">Çalışma zamanı sağlayıcısı, ana CLR ETW sağlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="54cf2-109">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="54cf2-110">CLR çalışma zamanı sağlayıcısı GUID 'SI e13c0d23-CCBC-4e12-931B-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="54cf2-110">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="54cf2-111">CLR ETW olaylarını yaygın olarak kullanılabilen araçları kullanarak günlüğe kaydetme ve görüntüleme örnekleri için bkz. [.NET Framework günlüğünü denetleme](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="54cf2-111">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
 <span data-ttu-id="54cf2-112">Gibi anahtar sözcüklerin `LoaderKeyword`kullanılmasına ek olarak, çok sık ortaya çıkarılan olayları günlüğe kaydetmek için anahtar kelimeleri etkinleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-112">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="54cf2-113">Ve anahtar sözcükleri bu olayları etkinleştirir ve [CLR ETW anahtar sözcükleri ve düzeylerinde](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)özetlenmektedir. `EndEnumerationKeyword` `StartEnumerationKeyword`</span><span class="sxs-lookup"><span data-stu-id="54cf2-113">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="54cf2-114">Özet sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="54cf2-114">The Rundown Provider</span></span>  
 <span data-ttu-id="54cf2-115">Özet sağlayıcının belirli özel amaçlı kullanımlar için açık olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-115">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="54cf2-116">Ancak, çoğu kullanıcı için çalışma zamanı sağlayıcısı yeterli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="54cf2-116">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="54cf2-117">CLR özeti sağlayıcısı GUID 'SI A669021C-C450-4609-A035-5AF59AF4DF18.</span><span class="sxs-lookup"><span data-stu-id="54cf2-117">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="54cf2-118">Normalde, bir işlem başlatılmadan önce ETW günlüğü etkinleştirilir ve işlem çıktıktan sonra günlüğe kaydetme kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="54cf2-118">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="54cf2-119">Ancak, işlem yürütülürken ETW günlüğü açıksa, işlem hakkında ek bilgiler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-119">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="54cf2-120">Örneğin, sembol çözümlemesi için, günlük kaydı açılmadan önce zaten yüklenmiş olan yöntemler için yöntem olaylarını günlüğe yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-120">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="54cf2-121">`DCStart` Ve`DCEnd` olayları, veri toplama başlatıldığında ve durdurulduğunda işlemin durumunu yakalar.</span><span class="sxs-lookup"><span data-stu-id="54cf2-121">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="54cf2-122">(Durum, zaten tam zamanında (JıT) derlenmiş Yöntemler ve yüklenmiş derlemeler dahil olmak üzere yüksek düzeyde bilgi anlamına gelir.) Bu iki olay, işlemde zaten ne olduğunu hakkında bilgi sağlayabilir; Örneğin, JıT olarak derlenen Yöntemler ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="54cf2-122">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="54cf2-123">Yalnızca `DC` ,`DCStart`,, veya`DCInit` adlarında bulunan olaylar, Özet sağlayıcının altında oluşturulur. `DCEnd`</span><span class="sxs-lookup"><span data-stu-id="54cf2-123">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="54cf2-124">Ayrıca, bu olaylar yalnızca Özet sağlayıcının altında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="54cf2-124">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="54cf2-125">Olay anahtar sözcük filtrelerine ek olarak, runaşağı sağlayıcı hedeflenen filtreleme sağlamak için `StartRundownKeyword` ve `EndRundownKeyword` anahtar kelimelerini de destekler.</span><span class="sxs-lookup"><span data-stu-id="54cf2-125">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="54cf2-126">Özeti Başlat</span><span class="sxs-lookup"><span data-stu-id="54cf2-126">Start Rundown</span></span>  
 <span data-ttu-id="54cf2-127">Bir başlangıç Özeti, runaşağı sağlayıcısı altında günlüğe kaydetme `StartRundownKeyword` anahtar sözcüğüyle etkinleştirildiğinde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-127">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="54cf2-128">Bu, `DCStart` etkinliğin oluşturulmasına neden olur ve sistemin durumunu yakalar.</span><span class="sxs-lookup"><span data-stu-id="54cf2-128">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="54cf2-129">Numaralandırma başlamadan önce `DCStartInit` olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-129">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="54cf2-130">Numaralandırmanın sonunda, `DCStartComplete` olay, veri toplamanın normal olarak sonlandırıldığı denetleyiciye bildirmek için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="54cf2-130">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="54cf2-131">Özeti Sonlandır</span><span class="sxs-lookup"><span data-stu-id="54cf2-131">End Rundown</span></span>  
 <span data-ttu-id="54cf2-132">Özet oluşturma sağlayıcısı altında günlüğe kaydetme, `EndRundownKeyword` anahtar sözcüğüyle etkinleştirildiği zaman bir bitiş Özeti tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-132">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="54cf2-133">Özeti Sonlandır, yürütülmeye devam eden bir işlemde profil oluşturmayı durduruyor.</span><span class="sxs-lookup"><span data-stu-id="54cf2-133">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="54cf2-134">`DCEnd` Olaylar, profil oluşturma durdurulduğunda sistemin durumunu yakalar.</span><span class="sxs-lookup"><span data-stu-id="54cf2-134">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="54cf2-135">Numaralandırma başlamadan önce `DCEndInit` olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-135">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="54cf2-136">Sabit listesinin sonunda, `DCEndComplete` bu olay, tüketiciye veri toplamanın normal şekilde sonlandırıldığını bildirmek için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="54cf2-136">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="54cf2-137">Başlangıç özeti ve bitiş Özeti öncelikle yönetilen sembol çözümlemesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54cf2-137">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="54cf2-138">Özeti Başlat, profil oluşturma oturumu başlatılmadan önce zaten JıT olarak derlenen yöntemler için adres aralığı bilgisi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-138">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="54cf2-139">Özet sonu, profil oluşturma işlemi kapalı olduğunda JıT derlenen tüm yöntemler için adres aralığı bilgisi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-139">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="54cf2-140">Bir profil oluşturma oturumu durdurulduğunda, Özeti Sonlandır işlemi otomatik olarak gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="54cf2-140">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="54cf2-141">Bunun yerine, yönetilen sembol çözünürlüğünü gerçekleştirmeye yönelik bir aracın, profil oluşturma durdurulmadan hemen önce, `EndRundownKeyword` anahtar sözcüğü etkin bir clr özet sağlayıcısı oturumunu açıkça çağırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-141">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="54cf2-142">Başlangıç Özeti veya bitiş Özeti, yönetilen sembol çözümlemesi için yöntem adres aralığı bilgilerini sağlayabilse de, `EndRundownKeyword` `StartRundownKeyword` anahtar sözcüğü yerine anahtar sözcüğü (olayları temin `DCEnd` eder) kullanmanızı öneririz ( etkinlikleri `DCStart` sağlar).</span><span class="sxs-lookup"><span data-stu-id="54cf2-142">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="54cf2-143">Kullanmak `StartRundownKeyword` , profil oluşturma oturumu sırasında Özet 'in profili oluşturulan senaryoyu rahatsız eden bir şekilde oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="54cf2-143">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="54cf2-144">Çalışma zamanı ve Özet sağlayıcıları kullanılarak ETW veri toplama</span><span class="sxs-lookup"><span data-stu-id="54cf2-144">ETW Data Collection Using Runtime and Rundown Providers</span></span>  
 <span data-ttu-id="54cf2-145">Aşağıdaki örnek, CLR özet sağlayıcısının, işlemlerin profil oluşturulmuş pencerenin içinde mi yoksa dışında mı başlayıp bitmediğine bakılmaksızın, en az etkiyle yönetilen işlemlerin sembol çözümüne izin veren bir şekilde nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-145">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1. <span data-ttu-id="54cf2-146">CLR Runtime sağlayıcısını kullanarak ETW günlüğünü açın:</span><span class="sxs-lookup"><span data-stu-id="54cf2-146">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```console
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     <span data-ttu-id="54cf2-147">Günlük, clr1. etl dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-147">The log will be saved to the clr1.etl file.</span></span>  
  
2. <span data-ttu-id="54cf2-148">İşlem yürütülmeye devam ederken profil oluşturmayı durdurmak için, `DCEnd` olay yakalamak üzere runaşağı sağlayıcısını başlatın:</span><span class="sxs-lookup"><span data-stu-id="54cf2-148">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```console
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     <span data-ttu-id="54cf2-149">Bu, `DCEnd` olay koleksiyonunun bir Özet oturum başlatmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="54cf2-149">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="54cf2-150">Tüm olayların toplanması için 30 ila 60 saniye beklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-150">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="54cf2-151">Günlük, clr1. ET2 dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-151">The log will be saved to the clr1.et2 file.</span></span>  
  
3. <span data-ttu-id="54cf2-152">Tüm ETW profil oluşturmayı kapat:</span><span class="sxs-lookup"><span data-stu-id="54cf2-152">Turn off all ETW profiling:</span></span>  
  
    ```console
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4. <span data-ttu-id="54cf2-153">Tek bir günlük dosyası oluşturmak için profilleri birleştirin:</span><span class="sxs-lookup"><span data-stu-id="54cf2-153">Merge the profiles to create one log file:</span></span>  
  
    ```console
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="54cf2-154">Birleştirilmiş. etl dosyası çalışma zamanı ve özet sağlayıcı oturumlarından olayları içerecektir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-154">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="54cf2-155">Bir araç, bir Kullanıcı profil oluşturmayı istemesi durumunda profil oluşturmayı hemen kapatmak yerine 2 ve 3. adımları (bir Özet oturumu başlatıp profil oluşturmayı sonlandırıp) yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-155">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="54cf2-156">Bir araç, 4. adımı da yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="54cf2-156">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54cf2-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54cf2-157">See also</span></span>

- [<span data-ttu-id="54cf2-158">Ortak Dil Çalışma Zamanı Modülünde ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="54cf2-158">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
