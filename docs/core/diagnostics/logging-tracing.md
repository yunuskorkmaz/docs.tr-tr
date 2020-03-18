---
title: Günlük ve izleme - .NET Core
description: .NET Core günlüğe kaydetme ve izleme için bir giriş.
ms.date: 08/05/2019
ms.openlocfilehash: 392b88c9ea3c31c919a605ac0a5c886f7d63f79a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714417"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="daba6-103">.NET Core günlük ve izleme</span><span class="sxs-lookup"><span data-stu-id="daba6-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="daba6-104">Günlük ve izleme gerçekten aynı teknik için iki isim vardır.</span><span class="sxs-lookup"><span data-stu-id="daba6-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="daba6-105">Basit teknik bilgisayarların ilk günlerinden beri kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="daba6-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="daba6-106">Sadece daha sonra tüketilecek çıktı yazmak için bir uygulama enstrümante içerir.</span><span class="sxs-lookup"><span data-stu-id="daba6-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="daba6-107">Günlüğe kaydetme ve izleme yi kullanma nedenleri</span><span class="sxs-lookup"><span data-stu-id="daba6-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="daba6-108">Bu basit teknik şaşırtıcı derecede güçlüdür.</span><span class="sxs-lookup"><span data-stu-id="daba6-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="daba6-109">Hata ayıklamanın başarısız olduğu durumlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="daba6-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="daba6-110">Uzun süreler boyunca meydana gelen sorunlar, geleneksel bir hata ayıklama ile hata ayıklamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="daba6-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="daba6-111">Günlükler, uzun sürelere yayılan ayrıntılı otopsi incelemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="daba6-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="daba6-112">Buna karşılık, hata ayıklayıcılar gerçek zamanlı analiz için sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="daba6-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="daba6-113">Çok iş parçacığı uygulamaları ve dağıtılmış uygulamalar genellikle hata ayıklamak zordur.</span><span class="sxs-lookup"><span data-stu-id="daba6-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="daba6-114">Hata ayıklama ekleme, davranışları değiştirme eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="daba6-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="daba6-115">Karmaşık sistemleri anlamak için gerektiğinde ayrıntılı günlükler analiz edilebilir.</span><span class="sxs-lookup"><span data-stu-id="daba6-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="daba6-116">Dağıtılmış uygulamalardaki sorunlar birçok bileşen arasındaki karmaşık etkileşimden kaynaklanabilir ve bir hata ayıkıcıyı sistemin her bölümüne bağlamak makul olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="daba6-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="daba6-117">Birçok hizmet oyalanmış olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="daba6-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="daba6-118">Hata ayıklama eklemek genellikle zaman arızası hatalarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="daba6-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="daba6-119">Sorunlar her zaman öngörülmüyor.</span><span class="sxs-lookup"><span data-stu-id="daba6-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="daba6-120">Günlüğe kaydetme ve izleme, bir sorun oluşması durumunda programların her zaman kaydedilebilmeleri için düşük ek iş yükü için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="daba6-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="daba6-121">.NET Çekirdek API'leri</span><span class="sxs-lookup"><span data-stu-id="daba6-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="daba6-122">Yazdırma stili API'leri</span><span class="sxs-lookup"><span data-stu-id="daba6-122">Print style APIs</span></span>

<span data-ttu-id="daba6-123">, <xref:System.Console?displayProperty=nameWithType> <xref:System.Diagnostics.Trace?displayProperty=nameWithType>ve <xref:System.Diagnostics.Debug?displayProperty=nameWithType> sınıfların her biri günlük için uygun benzer yazdırma stili API'leri sağlar.</span><span class="sxs-lookup"><span data-stu-id="daba6-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="daba6-124">Hangi yazdırma stili API'sini kullanacağınız seçim size kalmış.</span><span class="sxs-lookup"><span data-stu-id="daba6-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="daba6-125">Önemli farklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="daba6-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="daba6-126">Her zaman etkin ve her zaman konsola yazıyor.</span><span class="sxs-lookup"><span data-stu-id="daba6-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="daba6-127">Müşterinizin sürümde görmesi gerekebileceği bilgiler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="daba6-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="daba6-128">En basit yaklaşım olduğu için, genellikle geçici hata ayıklama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="daba6-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="daba6-129">Bu hata ayıklama kodu genellikle kaynak denetimi için iade asla.</span><span class="sxs-lookup"><span data-stu-id="daba6-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="daba6-130">Yalnızca tanımlandığında `TRACE` etkindir.</span><span class="sxs-lookup"><span data-stu-id="daba6-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="daba6-131">Ekli yazar <xref:System.Diagnostics.Trace.Listeners>, varsayılan <xref:System.Diagnostics.DefaultTraceListener>olarak .</span><span class="sxs-lookup"><span data-stu-id="daba6-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="daba6-132">Çoğu yapıda etkin olacak günlükleri oluştururken bu API'yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="daba6-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="daba6-133">Yalnızca tanımlandığında `DEBUG` etkindir.</span><span class="sxs-lookup"><span data-stu-id="daba6-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="daba6-134">Ekli hata ayıklama için yazıyor.</span><span class="sxs-lookup"><span data-stu-id="daba6-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="daba6-135">`COMPlus_DebugWriteToStdErr` Ayarlanırsa `*nix` stderr'a yazar.</span><span class="sxs-lookup"><span data-stu-id="daba6-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="daba6-136">Yalnızca hata ayıklama yapılarında etkinleştirilecek günlükleri oluştururken bu API'yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="daba6-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="daba6-137">Olayları kaydetme</span><span class="sxs-lookup"><span data-stu-id="daba6-137">Logging events</span></span>

<span data-ttu-id="daba6-138">Aşağıdaki API'ler daha fazla olay odaklıdır.</span><span class="sxs-lookup"><span data-stu-id="daba6-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="daba6-139">Basit dizeleri günlüğe kaydetmek yerine olay nesnelerini kaydederler.</span><span class="sxs-lookup"><span data-stu-id="daba6-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="daba6-140">EventSource birincil kök .NET Çekirdek izleme API'si.</span><span class="sxs-lookup"><span data-stu-id="daba6-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="daba6-141">Tüm .NET Standart sürümlerinde mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="daba6-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="daba6-142">Yalnızca seri leştirilebilir nesnelerin izlenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="daba6-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="daba6-143">Ekli [olay dinleyicilerine](xref:System.Diagnostics.Tracing.EventListener)yazar.</span><span class="sxs-lookup"><span data-stu-id="daba6-143">Writes to the attached [event listeners](xref:System.Diagnostics.Tracing.EventListener).</span></span>
  - <span data-ttu-id="daba6-144">.NET Core dinleyici sağlar:</span><span class="sxs-lookup"><span data-stu-id="daba6-144">.NET Core provides listeners for:</span></span>
    - <span data-ttu-id="daba6-145">.NET Core'un EventPipe'ı tüm platformlarda</span><span class="sxs-lookup"><span data-stu-id="daba6-145">.NET Core's EventPipe on all platforms</span></span>
    - [<span data-ttu-id="daba6-146">Windows için Olay İzleme (ETW)</span><span class="sxs-lookup"><span data-stu-id="daba6-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="daba6-147">LTTng Linux için izleme çerçevesi</span><span class="sxs-lookup"><span data-stu-id="daba6-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="daba6-148">.NET Core'a ve .NET Framework için [NuGet paketine](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) dahildir.</span><span class="sxs-lookup"><span data-stu-id="daba6-148">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="daba6-149">Seri olmayan nesnelerin işlem içinde izlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="daba6-149">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="daba6-150">Günlüğe kaydedilmiş nesnelerin seçili alanlarının bir 'e <xref:System.Diagnostics.Tracing.EventSource>yazılmasına izin veren bir köprü içerir.</span><span class="sxs-lookup"><span data-stu-id="daba6-150">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="daba6-151">Belirli bir etkinlik veya işlemden kaynaklanan günlük iletilerini tanımlamak için kesin bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="daba6-151">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="daba6-152">Bu nesne, farklı hizmetler arasında günlükleri ilişkilendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="daba6-152">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="daba6-153">Yalnızca Windows.</span><span class="sxs-lookup"><span data-stu-id="daba6-153">Windows only.</span></span>
  - <span data-ttu-id="daba6-154">Windows Olay Günlüğü'ne ileti yazar.</span><span class="sxs-lookup"><span data-stu-id="daba6-154">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="daba6-155">Sistem yöneticileri, Windows Olay Günlüğü'nde önemli uygulama hatası iletilerinin görünmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="daba6-155">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="daba6-156">ILogger ve günlük çerçeveleri</span><span class="sxs-lookup"><span data-stu-id="daba6-156">ILogger and logging frameworks</span></span>

<span data-ttu-id="daba6-157">Düşük düzeyli API'ler günlük gereksinimleriniz için doğru seçim olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="daba6-157">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="daba6-158">Bir günlük çerçevesi düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="daba6-158">You may want to consider a logging framework.</span></span>

<span data-ttu-id="daba6-159">Arabirim, <xref:Microsoft.Extensions.Logging.ILogger> loggers bağımlılık enjeksiyonu ile takılabilir ortak bir günlük arabirimi oluşturmak için kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="daba6-159">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="daba6-160">Örneğin, uygulamanız `ASP.NET` için en iyi seçimi yapabilmenize izin vermek için yerleşik ve üçüncü taraf çerçeveleri bir seçim için destek sunar:</span><span class="sxs-lookup"><span data-stu-id="daba6-160">For instance, to allow you to make the best choice for your application `ASP.NET` offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="daba6-161">ASP.NET günlük sağlayıcılar yerleşik</span><span class="sxs-lookup"><span data-stu-id="daba6-161">ASP.NET built in logging providers</span></span>](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [<span data-ttu-id="daba6-162">ASP.NET Üçüncü taraf günlük sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="daba6-162">ASP.NET Third-party logging providers</span></span>](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="daba6-163">İlgili başvuruları günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="daba6-163">Logging related references</span></span>

- [<span data-ttu-id="daba6-164">Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="daba6-164">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="daba6-165">Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="daba6-165">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="daba6-166">[ASP.NET Günlük,](/aspnet/core/fundamentals/logging) desteklediği günlük leme tekniklerine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="daba6-166">[ASP.NET Logging](/aspnet/core/fundamentals/logging) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="daba6-167">[C# String Enterpolasyonu](../../csharp/language-reference/tokens/interpolated.md) günlük kodu yazmayı basitleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="daba6-167">[C# String Interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- <span data-ttu-id="daba6-168">Özellik, <xref:System.Exception.Message?displayProperty=nameWithType> özel durumlar günlüğe kaydetme için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="daba6-168">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="daba6-169">Sınıf <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> günlükleri yığın bilgi sağlamak için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="daba6-169">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="daba6-170">Performansla ilgili önemli noktalar</span><span class="sxs-lookup"><span data-stu-id="daba6-170">Performance considerations</span></span>

<span data-ttu-id="daba6-171">Dize biçimlendirme fark edilir CPU işleme süresi alabilir.</span><span class="sxs-lookup"><span data-stu-id="daba6-171">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="daba6-172">Performans açısından kritik uygulamalarda şunları önermeniz önerilir:</span><span class="sxs-lookup"><span data-stu-id="daba6-172">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="daba6-173">Kimse dinlemezken çok sayıda günlüğe kaydetmekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="daba6-173">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="daba6-174">Önce günlüğe kaydetme nin etkin olup olmadığını denetleyerek maliyetli günlük iletileri oluşturmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="daba6-174">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="daba6-175">Yalnızca yararlı olanı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="daba6-175">Only log what's useful.</span></span>
- <span data-ttu-id="daba6-176">Süslü biçimlendirmeyi analiz aşamasına erteler.</span><span class="sxs-lookup"><span data-stu-id="daba6-176">Defer fancy formatting to the analysis stage.</span></span>
