---
title: Günlüğe kaydetme ve izleme-.NET Core
description: .NET Core günlüğe kaydetme ve izlemeye giriş.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 46e64a7f60b88c26ceef9ac817be885bfa180c8e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926358"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="1f4f1-103">.NET Core günlüğe kaydetme ve izleme</span><span class="sxs-lookup"><span data-stu-id="1f4f1-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="1f4f1-104">Günlüğe kaydetme ve izleme aynı teknik için gerçekten iki isimdir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="1f4f1-105">Basit teknik, bilgisayarların erken günlerinde bu yana kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="1f4f1-106">Bu, daha sonra tüketilen çıktıyı yazmak için bir uygulamanın seçilmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="1f4f1-107">Günlüğe kaydetme ve izlemeyi kullanma nedenleri</span><span class="sxs-lookup"><span data-stu-id="1f4f1-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="1f4f1-108">Bu basit teknik, her ne kadar güçlü bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="1f4f1-109">Bir hata ayıklayıcının başarısız olduğu durumlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1f4f1-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="1f4f1-110">Uzun süreler boyunca oluşan sorunlar, geleneksel hata ayıklayıcı ile hata ayıklama zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="1f4f1-111">Günlükler, uzun sürelerle ilgili ayrıntılı son mortem incelemesi için izin verir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="1f4f1-112">Buna karşılık, hata ayıklayıcılar gerçek zamanlı Analize göre kısıtlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="1f4f1-113">Çok iş parçacıklı uygulamalar ve dağıtılmış uygulamalar genellikle hata ayıklama için zordur.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="1f4f1-114">Hata ayıklayıcı eklemek, davranışları değiştirme eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="1f4f1-115">Ayrıntılı Günlükler, karmaşık sistemleri anlamak için gerektiği şekilde analiz edilebilir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="1f4f1-116">Dağıtılmış uygulamalardaki sorunlar birçok bileşen arasındaki karmaşık bir etkileşime neden olabilir ve bir hata ayıklayıcıyı sistemin her bölümüne bağlamak mantıklı olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="1f4f1-117">Birçok hizmet durdurulmuş olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="1f4f1-118">Hata ayıklayıcı iliştirmek genellikle zaman aşımı hatalarıyla neden olur.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="1f4f1-119">Sorunlar her zaman öngörülemeyen değildir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="1f4f1-120">Günlüğe kaydetme ve izleme düşük yük için tasarlanmıştır, böylece bir sorun oluşması durumunda programlar her zaman kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="1f4f1-121">.NET Core API 'Leri</span><span class="sxs-lookup"><span data-stu-id="1f4f1-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="1f4f1-122">Yazdırma stili API 'Leri</span><span class="sxs-lookup"><span data-stu-id="1f4f1-122">Print style APIs</span></span>

<span data-ttu-id="1f4f1-123"><xref:System.Console?displayProperty=nameWithType>, Ve <xref:System.Diagnostics.Trace?displayProperty=nameWithType> sınıflarınınherbiri,günlüğekaydetmeiçinuygun<xref:System.Diagnostics.Debug?displayProperty=nameWithType> olan benzer yazdırma stili API 'leri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="1f4f1-124">Hangi yazdırma stili API 'sinin kullanılması tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="1f4f1-125">Temel farklılıklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1f4f1-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="1f4f1-126">Her zaman etkin ve her zaman konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="1f4f1-127">Müşterinizin yayında görmeniz gerekebilecek bilgiler için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="1f4f1-128">En basit yaklaşım olduğundan, genellikle geçici geçici hata ayıklama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="1f4f1-129">Bu hata ayıklama kodu genellikle kaynak denetimine hiçbir zaman iade edilmedi.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="1f4f1-130">Yalnızca tanımlı olduğunda `TRACE` etkindir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="1f4f1-131">Varsayılan olarak, <xref:System.Diagnostics.Trace.Listeners> <xref:System.Diagnostics.DefaultTraceListener>ekli öğesine yazar.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="1f4f1-132">Çoğu derlemelerde etkinleştirilecek günlükleri oluştururken bu API 'YI kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="1f4f1-133">Yalnızca tanımlı olduğunda `DEBUG` etkindir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="1f4f1-134">Ekli bir hata ayıklayıcıya yazar.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="1f4f1-135">Ayarlandıysa ,`COMPlus_DebugWriteToStdErr` stderr 'e `*nix` yazma işlemleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="1f4f1-136">Yalnızca hata ayıklama yapılarında etkinleştirilecek günlükleri oluştururken bu API 'YI kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="1f4f1-137">Olayları günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="1f4f1-137">Logging events</span></span>

<span data-ttu-id="1f4f1-138">Aşağıdaki API 'Ler daha fazla olay yönelimlidir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="1f4f1-139">Basit dizeleri günlüğe kaydetmek yerine olay nesnelerini günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="1f4f1-140">EventSource birincil kök .NET Core izleme API 'sidir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="1f4f1-141">Tüm .NET Standard sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="1f4f1-142">Yalnızca seri hale getirilebilir nesnelerin izlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="1f4f1-143">Ekli [olay dinleyicilerine](xref:System.Diagnostics.Tracing.EventListener)yazar.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-143">Writes to the attached [event listeners](xref:System.Diagnostics.Tracing.EventListener).</span></span>
  - <span data-ttu-id="1f4f1-144">.NET Core için dinleyicileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="1f4f1-144">.NET Core provides listeners for:</span></span>
    - <span data-ttu-id="1f4f1-145">Tüm platformlarda .NET Core EventPipe</span><span class="sxs-lookup"><span data-stu-id="1f4f1-145">.NET Core's EventPipe on all platforms</span></span>
    - [<span data-ttu-id="1f4f1-146">Windows için olay Izleme (ETW)</span><span class="sxs-lookup"><span data-stu-id="1f4f1-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="1f4f1-147">Linux için LTTng izleme çerçevesi</span><span class="sxs-lookup"><span data-stu-id="1f4f1-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="1f4f1-148">.NET Core 'a ve .NET Framework için bir [NuGet paketi](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) olarak eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-148">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="1f4f1-149">Seri hale getirilebilir olmayan nesnelerin işlem içi izlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-149">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="1f4f1-150">Günlüğe kaydedilen nesnelerin seçili alanlarının bir <xref:System.Diagnostics.Tracing.EventSource>öğesine yazılmasına izin veren bir köprü içerir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-150">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="1f4f1-151">Belirli bir etkinlik veya işlemden kaynaklanan günlük iletilerini belirlemek için kesin bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-151">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="1f4f1-152">Bu nesne, farklı hizmetlerde günlükleri ilişkilendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-152">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="1f4f1-153">Yalnızca Windows.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-153">Windows only.</span></span>
  - <span data-ttu-id="1f4f1-154">İletileri Windows olay günlüğü 'ne yazar.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-154">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="1f4f1-155">Sistem yöneticileri, önemli uygulama hata iletilerinin Windows olay günlüğünde görünmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-155">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="1f4f1-156">ILogger ve günlük çerçeveleri</span><span class="sxs-lookup"><span data-stu-id="1f4f1-156">ILogger and logging frameworks</span></span>

<span data-ttu-id="1f4f1-157">Düşük düzey API 'Ler, günlük gereksinimleriniz için doğru seçim olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-157">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="1f4f1-158">Bir günlük çerçevesini düşünmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-158">You may want to consider a logging framework.</span></span>

<span data-ttu-id="1f4f1-159"><xref:Microsoft.Extensions.Logging.ILogger> Arabirim, günlükçülerin bağımlılık ekleme yoluyla eklenebileceği ortak bir günlüğe kaydetme arabirimi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-159">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="1f4f1-160">Örneğin, uygulamanız `ASP.NET` için en iyi seçimi yapmanıza olanak tanımak için yerleşik ve üçüncü taraf çerçeveler için destek sunar:</span><span class="sxs-lookup"><span data-stu-id="1f4f1-160">For instance, to allow you to make the best choice for your application `ASP.NET` offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="1f4f1-161">ASP.NET yerleşik günlük sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="1f4f1-161">ASP.NET built in logging providers</span></span>](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [<span data-ttu-id="1f4f1-162">ASP.NET üçüncü taraf günlüğü sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="1f4f1-162">ASP.NET Third-party logging providers</span></span>](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="1f4f1-163">Günlüğe kaydetme ilgili başvurular</span><span class="sxs-lookup"><span data-stu-id="1f4f1-163">Logging related references</span></span>

- [<span data-ttu-id="1f4f1-164">Nasıl yapılır: Izleme ve hata ayıklama ile koşullu derleme</span><span class="sxs-lookup"><span data-stu-id="1f4f1-164">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="1f4f1-165">Nasıl yapılır: Uygulama koduna Izleme deyimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="1f4f1-165">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="1f4f1-166">[ASP.net günlüğü](/aspnet/core/fundamentals/logging) , desteklediği günlük tekniklerine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-166">[ASP.NET Logging](/aspnet/core/fundamentals/logging) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="1f4f1-167">Dize ilişkilendirme, günlük kodu yazmayı kolaylaştırabilir. [ C# ](../../csharp/language-reference/tokens/interpolated.md)</span><span class="sxs-lookup"><span data-stu-id="1f4f1-167">[C# String Interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- <span data-ttu-id="1f4f1-168">Özelliği <xref:System.Exception.Message?displayProperty=nameWithType> , özel durumları günlüğe kaydetmek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-168">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="1f4f1-169">Bu <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> sınıf, günlüklerinizi yığın bilgileri sağlamak için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-169">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="1f4f1-170">Performans değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="1f4f1-170">Performance considerations</span></span>

<span data-ttu-id="1f4f1-171">Dize biçimlendirmesi, fark edilebilir CPU işlem süresini alabilir.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-171">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="1f4f1-172">Performans açısından kritik uygulamalarda şunları yapmanız önerilir:</span><span class="sxs-lookup"><span data-stu-id="1f4f1-172">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="1f4f1-173">Hiç kimse dinlemediğinde çok fazla günlük tutulmasını önleyin.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-173">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="1f4f1-174">Önce günlük kaydının etkin olup olmadığını denetleyerek maliyetli günlük mesajları oluşturmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-174">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="1f4f1-175">Yalnızca yararlı olanları günlüğe kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-175">Only log what's useful.</span></span>
- <span data-ttu-id="1f4f1-176">Süslü biçimlendirmeyi analiz aşamasına erteleyin.</span><span class="sxs-lookup"><span data-stu-id="1f4f1-176">Defer fancy formatting to the analysis stage.</span></span>
