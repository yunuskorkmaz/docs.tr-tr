---
title: CLR ETW Sağlayıcılar
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
ms.openlocfilehash: 33ef7491c2bffeda4ef737ed8f826cdfbfbb119d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400080"
---
# <a name="clr-etw-providers"></a><span data-ttu-id="78191-102">CLR ETW Sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="78191-102">CLR ETW Providers</span></span>
<span data-ttu-id="78191-103">Ortak dil çalışma süresi (CLR) iki sağlayıcıdan sahiptir: çalışma zamanı sağlayıcısı ve genel kaçıp sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="78191-103">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="78191-104">Çalışma zamanı sağlayıcısı, hangi anahtar kelimelerin (etkinlik kategorileri) etkin olduğuna bağlı olarak olayları yükseltir.</span><span class="sxs-lookup"><span data-stu-id="78191-104">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="78191-105">Örneğin, `LoaderKeyword` anahtar kelimeyi etkinleştirerek yükleyici olaylarını toplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78191-105">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="78191-106">Windows (ETW) olayları için Olay İzleme, daha sonra virgülle ayrılmış değer (.csv) dosyalarında gerektiğinde sonradan işlenebilecek .etl uzantısı olan bir dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="78191-106">Event Tracing for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="78191-107">.etl dosyasının .csv dosyasına nasıl dönüştürüldüğü hakkında bilgi için [bkz.](controlling-logging.md)</span><span class="sxs-lookup"><span data-stu-id="78191-107">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="78191-108">Çalışma Zamanı Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="78191-108">The Runtime Provider</span></span>  
 <span data-ttu-id="78191-109">Çalışma zamanı sağlayıcısı ana CLR ETW sağlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="78191-109">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="78191-110">CLR çalışma zamanı sağlayıcısı GUID e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 olduğunu.</span><span class="sxs-lookup"><span data-stu-id="78191-110">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="78191-111">Yaygın olarak kullanılan araçları kullanarak CLR ETW olaylarını nasıl günlüğe kaydedip görüntüleyebilirsiniz, [bkz.](controlling-logging.md)</span><span class="sxs-lookup"><span data-stu-id="78191-111">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](controlling-logging.md).</span></span>  
  
 <span data-ttu-id="78191-112">Gibi anahtar kelimeler kullanmanın yanı `LoaderKeyword`sıra, çok sık gündeme getirilebilir olayları günlüğe kaydetme için anahtar kelimeleri etkinleştirmek zorunda kalabilir.</span><span class="sxs-lookup"><span data-stu-id="78191-112">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="78191-113">Ve `EndEnumerationKeyword` anahtar kelimeler bu olayları etkinleştirmek ve [CLR ETW Anahtar Kelimeler ve Düzeyleri](clr-etw-keywords-and-levels.md)özetlenir. `StartEnumerationKeyword`</span><span class="sxs-lookup"><span data-stu-id="78191-113">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="78191-114">Rundown Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="78191-114">The Rundown Provider</span></span>  
 <span data-ttu-id="78191-115">Bazı özel amaçlı kullanımlar için rundown sağlayıcısının açık olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="78191-115">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="78191-116">Ancak, kullanıcıların çoğunluğu için, çalışma zamanı sağlayıcısı yeterli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78191-116">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="78191-117">CLR tükenme sağlayıcısı GUID A669021C-C450-4609-A035-5AF59AF4DF18 olduğunu.</span><span class="sxs-lookup"><span data-stu-id="78191-117">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="78191-118">Normalde, bir işlem başlatılmadan önce ETW günlüğü etkinleştirilir ve işlem çıktıktan sonra günlüğe kaydetme kapatılır.</span><span class="sxs-lookup"><span data-stu-id="78191-118">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="78191-119">Ancak, işlem yürütülerken ETW günlüğe kaydetme açıksa, işlem hakkında ek bilgiler gerekir.</span><span class="sxs-lookup"><span data-stu-id="78191-119">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="78191-120">Örneğin, sembol çözünürlüğü için günlüğe kaydetmeden önce zaten yüklenen yöntemler için yöntem olaylarını günlüğe kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="78191-120">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="78191-121">Ve `DCStart` `DCEnd` olaylar, veri toplama başlatıldığında ve durdurulduğunda işlemin durumunu yakalar.</span><span class="sxs-lookup"><span data-stu-id="78191-121">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="78191-122">(Devlet zaten sadece-in-time (JIT) derlenmiş ve yüklenen derlemeler yöntemleri de dahil olmak üzere, yüksek düzeyde bilgi anlamına gelir.) Bu iki olay, süreç içinde zaten neler olduğu hakkında bilgi sağlayabilir; örneğin, hangi yöntemler JIT-derlenmiş ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="78191-122">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="78191-123">Yalnızca `DC`, , `DCStart` `DCEnd`, `DCInit` veya adlarındaki olaylar, rundown sağlayıcısı altında yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="78191-123">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="78191-124">Ayrıca, bu olaylar yalnızca rundown sağlayıcısı altında yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="78191-124">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="78191-125">Olay anahtar kelime filtreleri ek olarak, rundown `StartRundownKeyword` sağlayıcısı `EndRundownKeyword` da hedefli filtreleme sağlamak için ve anahtar kelimeler destekler.</span><span class="sxs-lookup"><span data-stu-id="78191-125">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="78191-126">Özeti Başlat</span><span class="sxs-lookup"><span data-stu-id="78191-126">Start Rundown</span></span>  
 <span data-ttu-id="78191-127">`StartRundownKeyword` Başlangıç özeti, anahtar kelimeyle birlikte, tükenme sağlayıcısının altında günlüğe kaydedildiğinde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="78191-127">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="78191-128">Bu, `DCStart` olayın yükseltilmesine neden olur ve sistemin durumunu yakalar.</span><span class="sxs-lookup"><span data-stu-id="78191-128">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="78191-129">Numaralandırma başlamadan `DCStartInit` önce, olay yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="78191-129">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="78191-130">Numaralandırma sonunda, `DCStartComplete` olay, veri toplamanın normal olarak sonlandırıldığını denetleyiciye bildirmek için yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="78191-130">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="78191-131">Özeti Sona Erdirme</span><span class="sxs-lookup"><span data-stu-id="78191-131">End Rundown</span></span>  
 <span data-ttu-id="78191-132">`EndRundownKeyword` Özet sağlayıcının altında günlüğe kaydetme anahtar kelimeyle etkinleştirildiğinde bir son özeti tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="78191-132">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="78191-133">Son özet, yürütmeye devam eden bir işlemde profil oluşturmayı durdurur.</span><span class="sxs-lookup"><span data-stu-id="78191-133">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="78191-134">Profil `DCEnd` oluşturma durdurulduğunda olaylar sistemin durumunu yakalar.</span><span class="sxs-lookup"><span data-stu-id="78191-134">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="78191-135">Numaralandırma başlamadan `DCEndInit` önce, olay yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="78191-135">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="78191-136">Numaralandırma sonunda, `DCEndComplete` olay veri toplama normal sona erdirilmiş olduğunu tüketicibildirmek için yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="78191-136">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="78191-137">Başlangıç özeti ve bitiş özeti öncelikle yönetilen sembol çözümü için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="78191-137">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="78191-138">Başlangıç özeti, profil oluşturma oturumu başlamadan önce zaten JIT tarafından derlenmiş olan yöntemler için adres aralığı bilgileri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="78191-138">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="78191-139">Son özet, profil oluşturma kapatılmak üzereyken JIT tarafından derlenen tüm yöntemler için adres aralığı bilgileri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="78191-139">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="78191-140">Profil oluşturma oturumu durdurulduğunda son özet otomatik olarak gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="78191-140">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="78191-141">Bunun yerine, yönetilen sembol çözümlemesi gerçekleştirmek isteyen bir araç, profil oluşturma `EndRundownKeyword` durdurulmadan hemen önce, anahtar kelime etkin leştirilmiş bir CLR özeti sağlayıcısı oturumunu açıkça çağırmak zorundadır.</span><span class="sxs-lookup"><span data-stu-id="78191-141">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="78191-142">Başlangıç özeti veya son özet yönetilen sembol çözümü için yöntem adresi aralığı bilgileri `EndRundownKeyword` sağlasa da, `DCEnd` `StartRundownKeyword` anahtar kelime (olayları sağlayan) yerine anahtar sözcüğü (olayları sağlayan) kullanmanızı öneririz (olayları sağlayan). `DCStart`</span><span class="sxs-lookup"><span data-stu-id="78191-142">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="78191-143">Profil `StartRundownKeyword` oluşturma oturumu sırasında özetin gerçekleşmesine neden olan bu durum profil senaryosunu bozabilir.</span><span class="sxs-lookup"><span data-stu-id="78191-143">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="78191-144">Runtime ve Rundown Sağlayıcıları Kullanarak ETW Veri Toplama</span><span class="sxs-lookup"><span data-stu-id="78191-144">ETW Data Collection Using Runtime and Rundown Providers</span></span>  
 <span data-ttu-id="78191-145">Aşağıdaki örnek, proseslerin profilli pencerenin içinde veya dışında başlayıp bitmesine bakılmaksızın, yönetilen işlemlerin en az etkiyle çözüme kavuşturulmasını sağlayacak şekilde CLR özet sağlayıcısının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="78191-145">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1. <span data-ttu-id="78191-146">CLR çalışma zamanı sağlayıcısını kullanarak ETW günlüğe kaydetmeyi açın:</span><span class="sxs-lookup"><span data-stu-id="78191-146">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```console
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl
    ```  
  
     <span data-ttu-id="78191-147">Günlük clr1.etl dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="78191-147">The log will be saved to the clr1.etl file.</span></span>  
  
2. <span data-ttu-id="78191-148">İşlem yürütmeye devam ederken profil oluşturmayı durdurmak için, `DCEnd` olayları yakalamak için özeti sağlayıcıyı başlatın:</span><span class="sxs-lookup"><span data-stu-id="78191-148">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```console
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl
    ```  
  
     <span data-ttu-id="78191-149">Bu, `DCEnd` olayların bir özeti oturumu başlatmak için bir koleksiyon sağlar.</span><span class="sxs-lookup"><span data-stu-id="78191-149">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="78191-150">Tüm etkinliklerin toplanması için 30 ila 60 saniye beklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="78191-150">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="78191-151">Günlük clr1.et2 dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="78191-151">The log will be saved to the clr1.et2 file.</span></span>  
  
3. <span data-ttu-id="78191-152">Tüm ETW profil oluşturmayı kapatın:</span><span class="sxs-lookup"><span data-stu-id="78191-152">Turn off all ETW profiling:</span></span>  
  
    ```console
    xperf -stop clrRundown
    xperf -stop clr  
    ```  
  
4. <span data-ttu-id="78191-153">Tek bir günlük dosyası oluşturmak için profilleri birleştirin:</span><span class="sxs-lookup"><span data-stu-id="78191-153">Merge the profiles to create one log file:</span></span>  
  
    ```console
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="78191-154">Birleştirilmiş.etl dosyası, çalışma saatindeki olayları ve özeti sağlayıcı oturumlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="78191-154">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="78191-155">Bir araç, kullanıcı profil oluşturmanın durdurulmasını istediğinde profil oluşturmayı hemen kapatmak yerine 2 ve 3 adımlarını (bir başlangıç oturumu başlatıp profil oluşturmayı sonlandırma) yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="78191-155">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="78191-156">Bir araç da adım 4 çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78191-156">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78191-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78191-157">See also</span></span>

- [<span data-ttu-id="78191-158">Ortak Dil Çalışma Zamanında ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="78191-158">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
