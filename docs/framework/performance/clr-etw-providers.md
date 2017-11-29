---
title: "CLR ETW Sağlayıcılar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 18353939108d58eb2aaffee97e059e4430b25e3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="clr-etw-providers"></a><span data-ttu-id="2f096-102">CLR ETW Sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="2f096-102">CLR ETW Providers</span></span>
<span data-ttu-id="2f096-103">Ortak dil çalışma zamanı (CLR) iki sağlayıcı vardır: çalışma zamanı sağlayıcısı ve özeti sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2f096-103">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="2f096-104">Çalışma zamanı sağlayıcısı bağlı olarak anahtar sözcükler (olayların kategorilerini) etkinleştirildiği olayları başlatır.</span><span class="sxs-lookup"><span data-stu-id="2f096-104">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="2f096-105">Etkinleştirerek yükleyici olayları gibi toplayabilirsiniz `LoaderKeyword` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2f096-105">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="2f096-106">Olay için Windows (ETW) olayları izleme, daha sonra gerektikçe virgülle ayrılmış değer (.csv) dosyalarında sonrası işlenebilir .etl uzantısına sahip bir dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2f096-106">Event tracking for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="2f096-107">.Etl dosyası bir .csv dosyasına dönüştürme hakkında daha fazla bilgi için bkz: [.NET Framework günlüğü denetleme](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="2f096-107">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="2f096-108">Çalışma zamanı sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="2f096-108">The Runtime Provider</span></span>  
 <span data-ttu-id="2f096-109">Çalışma zamanı sağlayıcısı ana CLR ETW sağlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="2f096-109">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="2f096-110">CLR çalışma zamanı GUID e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 sağlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="2f096-110">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="2f096-111">Oturum ve yaygın olarak kullanılabilen araçlar kullanarak CLR ETW olayları görüntülemek nasıl örnekleri için bkz: [.NET Framework günlüğü denetleme](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="2f096-111">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
 <span data-ttu-id="2f096-112">Anahtar sözcükler gibi kullanmanın yanı sıra `LoaderKeyword`, çok sık gerçekleştirilen olaylar günlüğe için anahtar sözcükleri etkinleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2f096-112">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="2f096-113">`StartEnumerationKeyword` Ve `EndEnumerationKeyword` anahtar sözcükler bu olayları etkinleştirmek ve içinde özetlenen [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2f096-113">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="2f096-114">Özeti sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="2f096-114">The Rundown Provider</span></span>  
 <span data-ttu-id="2f096-115">Belirli özel amaçlı kullanımları özeti sağlayıcısı açılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f096-115">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="2f096-116">Ancak, kullanıcıların çoğunluğunun için çalışma zamanı sağlayıcısı yeterli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2f096-116">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="2f096-117">CLR özeti GUID A669021C-C450-4609-A035-5AF59AF4DF18 sağlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="2f096-117">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="2f096-118">Normalde, bir işlem başlatır ve işlem çıktıktan sonra günlüğe kaydetme kapalı önce ETW günlük kaydı etkindir.</span><span class="sxs-lookup"><span data-stu-id="2f096-118">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="2f096-119">Ancak, işlem yürütülürken ETW günlük kaydı açıksa, işlemi hakkında ek bilgi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2f096-119">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="2f096-120">Örneğin, simge çözünürlüğü için yöntem olayları günlüğe kaydetme açık olduğu önce zaten yüklü yöntemleri için oturum gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f096-120">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="2f096-121">`DCStart` Ve `DCEnd` olayları yakalama işleminin durumunu veri toplama başlatıldığında ve durduruldu.</span><span class="sxs-lookup"><span data-stu-id="2f096-121">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="2f096-122">(Durumu yüklenen derlemeler ve sadece derlenmiş zamanında (JIT) zaten olan yöntemler de dahil olmak üzere yüksek bir düzeyde bilgi ifade eder.) Bu iki olay işlemde önce olanlar hakkında bilgiler sağlayabilir; Örneğin, hangi yöntemlerin JIT-derlenmiş vb. yoktu.</span><span class="sxs-lookup"><span data-stu-id="2f096-122">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="2f096-123">Yalnızca olaylarla `DC`, `DCStart`, `DCEnd`, veya `DCInit` adlarında özeti sağlayıcısı altında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2f096-123">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="2f096-124">Ayrıca bu olaylar yalnızca özeti sağlayıcısı altında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2f096-124">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="2f096-125">Olay anahtar sözcük filtreleri yanı sıra da özeti sağlayıcının desteklediği `StartRundownKeyword` ve `EndRundownKeyword` sağlamak için anahtar sözcükler hedeflenen filtreleme.</span><span class="sxs-lookup"><span data-stu-id="2f096-125">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="2f096-126">Özeti Başlat</span><span class="sxs-lookup"><span data-stu-id="2f096-126">Start Rundown</span></span>  
 <span data-ttu-id="2f096-127">Günlük kaydı özeti sağlayıcısı altında ile etkinleştirildiğinde başlangıç özeti tetiklenir `StartRundownKeyword` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2f096-127">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="2f096-128">Bu neden `DCStart` oluşturulması için olay ve sistem durumunu yakalar.</span><span class="sxs-lookup"><span data-stu-id="2f096-128">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="2f096-129">Numaralandırma başlamadan önce `DCStartInit` olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2f096-129">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="2f096-130">Numaralandırma sonunda `DCStartComplete` olayı veri toplama normal olarak sonlandı denetleyicisi bildirmek için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2f096-130">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="2f096-131">Son özeti</span><span class="sxs-lookup"><span data-stu-id="2f096-131">End Rundown</span></span>  
 <span data-ttu-id="2f096-132">Günlük kaydı özeti sağlayıcısı altında ile etkinleştirildiğinde son özeti tetiklenir `EndRundownKeyword` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2f096-132">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="2f096-133">Yürütmek için devam eden bir işlem profil son özeti durdurur.</span><span class="sxs-lookup"><span data-stu-id="2f096-133">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="2f096-134">`DCEnd` Profil durdurulduğunda sistem durumu olayları yakalar.</span><span class="sxs-lookup"><span data-stu-id="2f096-134">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="2f096-135">Numaralandırma başlamadan önce `DCEndInit` olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2f096-135">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="2f096-136">Numaralandırma sonunda `DCEndComplete` olayı veri toplama normal olarak sonlandı tüketici bildirmek için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2f096-136">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="2f096-137">Özeti başlangıç ve bitiş özeti temelde yönetilen simgesi çözümlemesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2f096-137">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="2f096-138">Başlangıç özeti profil oluşturma oturumu başlatıldı önce zaten JIT derlenmiş yöntemleri için adres aralığı bilgilerini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="2f096-138">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="2f096-139">Son özeti profil oluşturma hakkında kapatılmasına olduğunda JIT derlenmiş tüm yöntemleri için adres aralığı bilgilerini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="2f096-139">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="2f096-140">Profil oluşturma oturumu durdurulduğunda son özeti otomatik olarak gerçekleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="2f096-140">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="2f096-141">Bunun yerine, açıkça bir CLR özeti sağlayıcısı oturumla çağırmak yönetilen simgesi çözümlemesi arayan bir araç olan `EndRundownKeyword` anahtar sözcüğü yalnızca profil durdurulmadan önce etkin.</span><span class="sxs-lookup"><span data-stu-id="2f096-141">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="2f096-142">Başlangıç özeti ya da son özeti yönetilen simge çözünürlüğü için yöntemi adres aralığı bilgilerini sağlayabilir, ancak kullanmanızı öneririz `EndRundownKeyword` anahtar sözcüğü (hangi kaynakları `DCEnd` olayları) yerine `StartRundownKeyword` anahtar sözcüğü (hangi sağladığı `DCStart` olayları).</span><span class="sxs-lookup"><span data-stu-id="2f096-142">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="2f096-143">Kullanarak `StartRundownKeyword` profili senaryo rahatsız profil oluşturma oturumu sırasında gerçekleşecek şekilde özeti neden olur.</span><span class="sxs-lookup"><span data-stu-id="2f096-143">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="2f096-144">Çalışma zamanı ve özeti sağlayıcılarını kullanarak ETW veri toplama</span><span class="sxs-lookup"><span data-stu-id="2f096-144">ETW Data Collection Using Runtime and Rundown Providers</span></span>  
 <span data-ttu-id="2f096-145">Aşağıdaki örnek CLR özeti sağlayıcısının işlemleri başlatın veya profili penceresinin içinde veya dışında bitiş bağımsız olarak en az etkiyle yönetilen işlemlerin simge çözünürlüğü izin veren bir şekilde nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f096-145">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1.  <span data-ttu-id="2f096-146">CLR çalışma zamanı sağlayıcısı kullanarak ETW günlük özelliğini açın:</span><span class="sxs-lookup"><span data-stu-id="2f096-146">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     <span data-ttu-id="2f096-147">Günlük clr1.etl dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2f096-147">The log will be saved to the clr1.etl file.</span></span>  
  
2.  <span data-ttu-id="2f096-148">Yürütülecek işlem devam ederken profil oluşturmayı durdurmak için yakalamak için özeti sağlayıcı Başlat `DCEnd` olayları:</span><span class="sxs-lookup"><span data-stu-id="2f096-148">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     <span data-ttu-id="2f096-149">Bu koleksiyonu sağlar `DCEnd` özeti oturumu başlatmak için olaylar.</span><span class="sxs-lookup"><span data-stu-id="2f096-149">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="2f096-150">Tüm olayları toplanacak 30-60 saniye beklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2f096-150">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="2f096-151">Günlük clr1.et2 dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2f096-151">The log will be saved to the clr1.et2 file.</span></span>  
  
3.  <span data-ttu-id="2f096-152">Tüm ETW profil oluşturmayı Kapat:</span><span class="sxs-lookup"><span data-stu-id="2f096-152">Turn off all ETW profiling:</span></span>  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4.  <span data-ttu-id="2f096-153">Tek bir günlük dosyası oluşturmak için profillerini birleştirin:</span><span class="sxs-lookup"><span data-stu-id="2f096-153">Merge the profiles to create one log file:</span></span>  
  
    ```  
    xperf -merge -d clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="2f096-154">Çalışma zamanı ve özeti sağlayıcısı oturumları olayların merged.etl dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="2f096-154">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="2f096-155">Bir aracı hemen bir kullanıcı profil oluşturmayı kapatma yerine adım 2 ve 3 (özeti bir oturum açması ve profil oluşturma sonlandırma) yürütebilir durdurulacak profil istekleri.</span><span class="sxs-lookup"><span data-stu-id="2f096-155">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="2f096-156">Bir aracı ayrıca 4. adım yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="2f096-156">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f096-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2f096-157">See Also</span></span>  
 [<span data-ttu-id="2f096-158">Ortak dil çalışma zamanında ETW olayları</span><span class="sxs-lookup"><span data-stu-id="2f096-158">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
