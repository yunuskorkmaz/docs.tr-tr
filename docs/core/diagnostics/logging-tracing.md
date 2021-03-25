---
title: Günlüğe kaydetme ve izleme-.NET Core
description: .NET Core günlüğe kaydetme ve izlemeye giriş.
ms.date: 10/12/2020
ms.openlocfilehash: dfecdad4518c79b605eb4fbe991af07fcba7db1c
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111094"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="f5d5e-103">.NET Core günlüğe kaydetme ve izleme</span><span class="sxs-lookup"><span data-stu-id="f5d5e-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="f5d5e-104">Günlüğe kaydetme ve izleme aynı teknik için gerçekten iki isimdir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="f5d5e-105">Basit teknik, bilgisayarların erken günlerinde bu yana kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="f5d5e-106">Bu, daha sonra tüketilen çıktıyı yazmak için bir uygulamanın seçilmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="f5d5e-107">Günlüğe kaydetme ve izlemeyi kullanma nedenleri</span><span class="sxs-lookup"><span data-stu-id="f5d5e-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="f5d5e-108">Bu basit teknik şaşırtıcı bir biçimde güçlüdür.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="f5d5e-109">Bir hata ayıklayıcının başarısız olduğu durumlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="f5d5e-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="f5d5e-110">Uzun süre boyunca tekrar eden sorunları geleneksel bir hata ayıklayıcısıyla çözmek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="f5d5e-111">Günlükler, uzun sürelere yayılan ayrıntılı son durum incelemeleri yapmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="f5d5e-112">Buna karşın, hata ayıklayıcılar gerçek zamanlı analizle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="f5d5e-113">Çok iş parçacıklı ve dağıtılmış uygulamalarda hata ayıklamak genellikle zordur.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="f5d5e-114">Hata ayıklayıcıyı kullanıma açmak, davranışları değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="f5d5e-115">Ayrıntılı günlükler, karmaşık sistemleri anlamak için gerekli şekilde analiz edilebilir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="f5d5e-116">Dağıtılmış uygulamalardaki sorunlar, pek çok bileşen arasındaki karmaşık etkileşimden kaynaklanabilir ve sistemin her parçasına bir hata ayıklayıcısı eklemek mantıklı olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="f5d5e-117">Çok sayıda hizmetin durdurulmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="f5d5e-118">Hata ayıklayıcıyı kullanıma açmak genellikle zaman aşımı sorunlarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="f5d5e-119">Sorunlar her zaman öngörülemez.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="f5d5e-120">Günlüğe kaydetme ve izleme, sorun olması durumunda programların her zaman kayıt yapabilmesi için düşük ek yüke uygun şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="f5d5e-121">.NET Core API 'Leri</span><span class="sxs-lookup"><span data-stu-id="f5d5e-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="f5d5e-122">Yazdırma stili API 'Leri</span><span class="sxs-lookup"><span data-stu-id="f5d5e-122">Print style APIs</span></span>

<span data-ttu-id="f5d5e-123"><xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType> Ve <xref:System.Diagnostics.Debug?displayProperty=nameWithType> sınıflarının her biri, günlüğe kaydetme için uygun olan benzer yazdırma stili API 'leri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="f5d5e-124">Kullanılacak yazdırma stili API’si tercihi size bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="f5d5e-125">En önemli farklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f5d5e-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="f5d5e-126">Her zaman etkindir ve konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="f5d5e-127">Müşterilerinizin yayında görmeleri gerekebilecek bilgiler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="f5d5e-128">En basit yaklaşım bu olduğundan, genellikle geçici hata ayıklama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="f5d5e-129">Bu hata ayıklama kodu kaynak denetiminde neredeyse asla kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="f5d5e-130">Yalnızca `TRACE` , `#define TRACE` kaynağınıza eklenerek veya derlenirken seçeneği belirtilerek tanımlandığında etkindir `/d:TRACE` .</span><span class="sxs-lookup"><span data-stu-id="f5d5e-130">Only enabled when `TRACE` is defined by adding `#define TRACE` to your source or specifying the option `/d:TRACE` when compiling.</span></span>
  - <span data-ttu-id="f5d5e-131"><xref:System.Diagnostics.Trace.Listeners>Varsayılan olarak, ekli öğesine yazar <xref:System.Diagnostics.DefaultTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="f5d5e-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="f5d5e-132">Çoğu derlemede etkinleştirilecek olan günlükler oluştururken bu API’yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="f5d5e-133">Yalnızca `DEBUG` , `#define DEBUG` kaynağınıza eklenerek veya derlenirken seçeneği belirtilerek tanımlandığında etkindir `/d:DEBUG` .</span><span class="sxs-lookup"><span data-stu-id="f5d5e-133">Only enabled when `DEBUG` is defined by adding `#define DEBUG` to your source or specifying the option `/d:DEBUG` when compiling.</span></span>
  - <span data-ttu-id="f5d5e-134">Kullanıma açılan bir hata ayıklayıcıya yazar.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="f5d5e-135">`*nix`Ayarlandıysa, stderr 'e yazma işlemleri `COMPlus_DebugWriteToStdErr` yapılır.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="f5d5e-136">Yalnızca hata ayıklama derlemelerinde etkinleştirilecek günlükler oluştururken bu API’yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="f5d5e-137">Olayları günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="f5d5e-137">Logging events</span></span>

<span data-ttu-id="f5d5e-138">Aşağıdaki API 'Ler daha fazla olay yönelimlidir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="f5d5e-139">Basit dizeleri günlüğe kaydetmek yerine olay nesnelerini günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="f5d5e-140">EventSource birincil kök .NET Core izleme API 'sidir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="f5d5e-141">Tüm .NET Standard sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="f5d5e-142">Yalnızca seri hale getirilebilir nesnelerin izlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="f5d5e-143">, EventSource öğesini kullanmak için yapılandırılmış herhangi bir [EventListener](xref:System.Diagnostics.Tracing.EventListener) örneği aracılığıyla işlem içi tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-143">Can be consumed in-process via any [EventListener](xref:System.Diagnostics.Tracing.EventListener) instances configured to consume the EventSource.</span></span>
  - <span data-ttu-id="f5d5e-144">Şu yollarla işlem dışı tüketilebilir:</span><span class="sxs-lookup"><span data-stu-id="f5d5e-144">Can be consumed out-of-process via:</span></span>
    - <span data-ttu-id="f5d5e-145">Tüm platformlarda [.NET Core EventPipe](./eventpipe.md)</span><span class="sxs-lookup"><span data-stu-id="f5d5e-145">[.NET Core's EventPipe](./eventpipe.md) on all platforms</span></span>
    - [<span data-ttu-id="f5d5e-146">Windows için olay Izleme (ETW)</span><span class="sxs-lookup"><span data-stu-id="f5d5e-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="f5d5e-147">Linux için LTTng izleme çerçevesi</span><span class="sxs-lookup"><span data-stu-id="f5d5e-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)
      - <span data-ttu-id="f5d5e-148">İzlenecek yol: [PerfCollect kullanarak bir LTTng Izlemesi toplayın](trace-perfcollect-lttng.md).</span><span class="sxs-lookup"><span data-stu-id="f5d5e-148">Walkthrough: [Collect an LTTng trace using PerfCollect](trace-perfcollect-lttng.md).</span></span>

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="f5d5e-149">.NET Core 'a ve .NET Framework için bir [NuGet paketi](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) olarak eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-149">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="f5d5e-150">Seri hale getirilebilir olmayan nesnelerin işlem içi izlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-150">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="f5d5e-151">Günlüğe kaydedilen nesnelerin seçili alanlarının bir öğesine yazılmasına izin veren bir köprü içerir <xref:System.Diagnostics.Tracing.EventSource> .</span><span class="sxs-lookup"><span data-stu-id="f5d5e-151">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="f5d5e-152">Yalnızca Windows.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-152">Windows only.</span></span>
  - <span data-ttu-id="f5d5e-153">İletileri Windows olay günlüğü 'ne yazar.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-153">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="f5d5e-154">Sistem yöneticileri, önemli uygulama hata iletilerinin Windows olay günlüğünde görünmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-154">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="distributed-tracing"></a><span data-ttu-id="f5d5e-155">Dağıtılmış Izleme</span><span class="sxs-lookup"><span data-stu-id="f5d5e-155">Distributed Tracing</span></span>

<span data-ttu-id="f5d5e-156">[Dağıtılmış izleme](./distributed-tracing.md) , özellikle birden çok makineye veya işleme dağılmış olabilecek uygulamalarda hataları ve performans sorunlarını yerelleştirebilmenizi sağlayan bir tanılama tekniğidir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-156">[Distributed Tracing](./distributed-tracing.md) is a diagnostic technique that helps engineers localize failures and performance issues within applications, especially those that may be distributed across multiple machines or processes.</span></span> <span data-ttu-id="f5d5e-157">Bu teknik, farklı uygulama bileşenleri tarafından yapılan bir uygulamayla bir araya geçen ve başka bir iş tarafından, uygulamanın eşzamanlı istekler için yapmakta olabileceği diğer çalışmalardan ayıran istekleri izler.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-157">This technique tracks requests through an application correlating together work done by different application components and separating it from other work the application may be doing for concurrent requests.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="f5d5e-158">ILogger ve günlük çerçeveleri</span><span class="sxs-lookup"><span data-stu-id="f5d5e-158">ILogger and logging frameworks</span></span>

<span data-ttu-id="f5d5e-159">Düşük düzey API 'Ler, günlük gereksinimleriniz için doğru seçim olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-159">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="f5d5e-160">Bir günlük çerçevesini düşünmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-160">You may want to consider a logging framework.</span></span>

<span data-ttu-id="f5d5e-161"><xref:Microsoft.Extensions.Logging.ILogger>Arabirim, günlükçülerin bağımlılık ekleme yoluyla eklenebileceği ortak bir günlüğe kaydetme arabirimi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-161">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="f5d5e-162">Örneğin, uygulamanızın .NET için en iyi seçimi yapmanıza olanak tanımak üzere yerleşik ve üçüncü taraf çerçeveler için destek sunar:</span><span class="sxs-lookup"><span data-stu-id="f5d5e-162">For instance, to allow you to make the best choice for your application .NET offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="f5d5e-163">.NET yerleşik günlüğe kaydetme sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="f5d5e-163">.NET Built-in logging providers</span></span>](../extensions/logging-providers.md#built-in-logging-providers)
- [<span data-ttu-id="f5d5e-164">.NET üçüncü taraf günlüğü sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="f5d5e-164">.NET Third-party logging providers</span></span>](../extensions/logging-providers.md#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="f5d5e-165">Günlüğe kaydetme ilgili başvurular</span><span class="sxs-lookup"><span data-stu-id="f5d5e-165">Logging related references</span></span>

- [<span data-ttu-id="f5d5e-166">Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="f5d5e-166">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="f5d5e-167">Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="f5d5e-167">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="f5d5e-168">[.Net ' te oturum açmak](../extensions/logging.md) , desteklediği günlük tekniklerine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-168">[Logging in .NET](../extensions/logging.md) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="f5d5e-169">[C# dize ilişkilendirme](../../csharp/language-reference/tokens/interpolated.md) , günlük kodu yazmayı kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-169">[C# string interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- [<span data-ttu-id="f5d5e-170">Çalışma zamanı sağlayıcısı olay listesi</span><span class="sxs-lookup"><span data-stu-id="f5d5e-170">Runtime Provider Event List</span></span>](../../fundamentals/diagnostics/runtime-events.md)

- [<span data-ttu-id="f5d5e-171">.NET 'teki iyi bilinen olay sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="f5d5e-171">Well-known Event Providers in .NET</span></span>](well-known-event-providers.md)

- <span data-ttu-id="f5d5e-172"><xref:System.Exception.Message?displayProperty=nameWithType>Özelliği, özel durumları günlüğe kaydetmek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-172">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="f5d5e-173">Bu <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> sınıf, günlüklerinizi yığın bilgileri sağlamak için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-173">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="f5d5e-174">Performansla ilgili önemli noktalar</span><span class="sxs-lookup"><span data-stu-id="f5d5e-174">Performance considerations</span></span>

<span data-ttu-id="f5d5e-175">Dize biçimlendirmesi, fark edilebilir CPU işlem süresini alabilir.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-175">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="f5d5e-176">Performans açısından kritik uygulamalarda şunları yapmanız önerilir:</span><span class="sxs-lookup"><span data-stu-id="f5d5e-176">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="f5d5e-177">Hiç kimse dinlemediğinde çok fazla günlük tutulmasını önleyin.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-177">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="f5d5e-178">Önce günlük kaydının etkin olup olmadığını denetleyerek maliyetli günlük mesajları oluşturmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-178">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="f5d5e-179">Yalnızca yararlı olanları günlüğe kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-179">Only log what's useful.</span></span>
- <span data-ttu-id="f5d5e-180">Süslü biçimlendirmeyi analiz aşamasına erteleyin.</span><span class="sxs-lookup"><span data-stu-id="f5d5e-180">Defer fancy formatting to the analysis stage.</span></span>
