---
title: ​.NET Core 2.2’deki yenilikler
description: .NET Core 2.2'de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: 64cb561acd72ff5d4a11fcae7ce59eaad750f74e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644365"
---
# <a name="whats-new-in-net-core-22"></a><span data-ttu-id="acc9d-103">​.NET Core 2.2’deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="acc9d-103">What's new in .NET Core 2.2</span></span>

<span data-ttu-id="acc9d-104">.NET Core 2.2 uygulama dağıtımında geliştirmeler, çalışma zamanı hizmetleri için olay işleme, Azure SQL veritabanlarına kimlik doğrulama, `Main` JIT derleyici performansı ve yöntemin yürütülmesinden önce kod enjeksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="acc9d-104">.NET Core 2.2 includes enhancements in application deployment, event handling for runtime services, authentication to Azure SQL databases, JIT compiler performance, and code injection prior to the execution of the `Main` method.</span></span>

## <a name="new-deployment-mode"></a><span data-ttu-id="acc9d-105">Yeni dağıtım modu</span><span class="sxs-lookup"><span data-stu-id="acc9d-105">New deployment mode</span></span>

<span data-ttu-id="acc9d-106">.NET Core 2.2 ile başlayarak, **.dll** dosyaları yerine **.exe** dosyaları olan [çerçeveye bağımlı yürütülebilir öğeleri](../deploying/index.md#publish-runtime-dependent)dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc9d-106">Starting with .NET Core 2.2, you can deploy [framework-dependent executables](../deploying/index.md#publish-runtime-dependent), which are **.exe** files instead of **.dll** files.</span></span> <span data-ttu-id="acc9d-107">İşlevsel olarak çerçeveye bağımlı dağıtımlara benzer şekilde, çerçeveye bağımlı yürütülebilir (FDE) hala .NET Core'un çalıştırılacak ortak sistem genelindeki sürümünün varlığına güvenir.</span><span class="sxs-lookup"><span data-stu-id="acc9d-107">Functionally similar to framework-dependent deployments, framework-dependent executables (FDE) still rely on the presence of a shared system-wide version of .NET Core to run.</span></span> <span data-ttu-id="acc9d-108">Uygulamanız yalnızca kodunuzu ve üçüncü taraf bağımlılıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="acc9d-108">Your app contains only your code and any third-party dependencies.</span></span> <span data-ttu-id="acc9d-109">Çerçeveye bağımlı dağıtımların aksine, FD'ler platforma özgüdür.</span><span class="sxs-lookup"><span data-stu-id="acc9d-109">Unlike framework-dependent deployments, FDEs are platform-specific.</span></span>

<span data-ttu-id="acc9d-110">Bu yeni dağıtım modu, kitaplık yerine çalıştırılabilir bir uygulama oluşturmanın belirgin avantajına sahiptir, bu da uygulamanızı ilk önce aramadan `dotnet` doğrudan çalıştırabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="acc9d-110">This new deployment mode has the distinct advantage of building an executable instead of a library, which means you can run your app directly without invoking `dotnet` first.</span></span>

## <a name="core"></a><span data-ttu-id="acc9d-111">Çekirdek</span><span class="sxs-lookup"><span data-stu-id="acc9d-111">Core</span></span>

<span data-ttu-id="acc9d-112">**Çalışma zamanı hizmetlerinde olayları işleme**</span><span class="sxs-lookup"><span data-stu-id="acc9d-112">**Handling events in runtime services**</span></span>

<span data-ttu-id="acc9d-113">Uygulamanızı nasıl etkilediğini anlamak için uygulamanızın GC, JIT ve ThreadPool gibi çalışma zamanı hizmetlerini kullanımını sık sık izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc9d-113">You may often want to monitor your application's use of runtime services, such as the GC, JIT, and ThreadPool, to understand how they impact your application.</span></span><span data-ttu-id="acc9d-114">Windows sistemlerinde, bu genellikle geçerli işlemin ETW olayları izleyerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="acc9d-114"> On Windows systems, this is commonly done by monitoring the ETW events of the current process.</span></span><span data-ttu-id="acc9d-115">Bu durum iyi çalışmaya devam etse de, düşük ayrıcalıklı bir ortamda veya Linux veya macOS'ta çalışıyorsanız ETW'yi kullanmak her zaman mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="acc9d-115"> While this continues to work well, it's not always possible to use ETW if you're running in a low-privilege environment or on Linux or macOS.</span></span>

<span data-ttu-id="acc9d-116">.NET Core 2.2 ile başlayarak, CoreCLR <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> olayları artık sınıf kullanılarak tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="acc9d-116">Starting with .NET Core 2.2, CoreCLR events can now be consumed using the <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="acc9d-117">Bu olaylar GC, JIT, ThreadPool ve interop gibi runtime hizmetlerinin davranışını açıklar.</span><span class="sxs-lookup"><span data-stu-id="acc9d-117">These events describe the behavior of such runtime services as GC, JIT, ThreadPool, and interop.</span></span> <span data-ttu-id="acc9d-118">Bunlar CoreCLR ETW sağlayıcısının bir parçası olarak ortaya çıkan aynı olaylardır.</span><span class="sxs-lookup"><span data-stu-id="acc9d-118">These are the same events that are exposed as part of the CoreCLR ETW provider.</span></span><span data-ttu-id="acc9d-119">Bu, uygulamaların bu olayları tüketmesine veya bunları bir telemetri toplama hizmetine göndermek için bir aktarım mekanizması kullanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="acc9d-119">  This allows for applications to consume these events or use a transport mechanism to send them to a telemetry aggregation service.</span></span> <span data-ttu-id="acc9d-120">Aşağıdaki kod örneğinde olaylara nasıl abone olunur görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="acc9d-120">You can see how to subscribe to events in the following code sample:</span></span>

```csharp
internal sealed class SimpleEventListener : EventListener
{
    // Called whenever an EventSource is created.
    protected override void OnEventSourceCreated(EventSource eventSource)
    {
        // Watch for the .NET runtime EventSource and enable all of its events.
        if (eventSource.Name.Equals("Microsoft-Windows-DotNETRuntime"))
        {
            EnableEvents(eventSource, EventLevel.Verbose, (EventKeywords)(-1));
        }
    }

    // Called whenever an event is written.
    protected override void OnEventWritten(EventWrittenEventArgs eventData)
    {
        // Write the contents of the event to the console.
        Console.WriteLine($"ThreadID = {eventData.OSThreadId} ID = {eventData.EventId} Name = {eventData.EventName}");
        for (int i = 0; i < eventData.Payload.Count; i++)
        {
            string payloadString = eventData.Payload[i]?.ToString() ?? string.Empty;
            Console.WriteLine($"\tName = \"{eventData.PayloadNames[i]}\" Value = \"{payloadString}\"");
        }
        Console.WriteLine("\n");
    }
}
```

<span data-ttu-id="acc9d-121">Buna ek olarak, .NET Core 2.2, <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> ETW olayları hakkında ek bilgi sağlamak için sınıfa aşağıdaki iki özelliği ekler:</span><span class="sxs-lookup"><span data-stu-id="acc9d-121">In addition, .NET Core 2.2 adds the following two properties to the <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> class to provide additional information about ETW events:</span></span>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a><span data-ttu-id="acc9d-122">Veriler</span><span class="sxs-lookup"><span data-stu-id="acc9d-122">Data</span></span>

<span data-ttu-id="acc9d-123">**SqlConnection.AccessToken özelliğine sahip Azure SQL veritabanlarına AAD kimlik doğrulaması**</span><span class="sxs-lookup"><span data-stu-id="acc9d-123">**AAD authentication to Azure SQL databases with the SqlConnection.AccessToken property**</span></span>

<span data-ttu-id="acc9d-124">.NET Core 2.2 ile başlayarak, Azure Active Directory tarafından verilen bir erişim belirteci, bir Azure SQL veritabanına kimlik doğrulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="acc9d-124">Starting with .NET Core 2.2, an access token issued by Azure Active Directory can be used to authenticate to an Azure SQL database.</span></span> <span data-ttu-id="acc9d-125">Erişim belirteçlerini desteklemek <xref:System.Data.SqlClient.SqlConnection.AccessToken> için özellik sınıfa <xref:System.Data.SqlClient.SqlConnection> eklendi.</span><span class="sxs-lookup"><span data-stu-id="acc9d-125">To support access tokens, the <xref:System.Data.SqlClient.SqlConnection.AccessToken> property has been added to the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="acc9d-126">AAD kimlik doğrulamadan yararlanmak için System.Data.SqlClient NuGet paketinin 4.6 sürümünü indirin.</span><span class="sxs-lookup"><span data-stu-id="acc9d-126">To take advantage of AAD authentication, download version 4.6 of the System.Data.SqlClient NuGet package.</span></span> <span data-ttu-id="acc9d-127">Özelliği kullanmak için, [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet paketinde yer alan [.NET için Active Directory Authentication Library'yi](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) kullanarak erişim belirteci değerini elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc9d-127">In order to use the feature, you can obtain the access token value using the [Active Directory Authentication Library for .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contained in the [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet package.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="acc9d-128">JIT derleyici geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="acc9d-128">JIT compiler improvements</span></span>

<span data-ttu-id="acc9d-129">**Katmanlı derleme bir opt-in özelliği olmaya devam ediyor**</span><span class="sxs-lookup"><span data-stu-id="acc9d-129">**Tiered compilation remains an opt-in feature**</span></span>

<span data-ttu-id="acc9d-130">.NET Core 2.1'de, JIT derleyicisi yeni bir derleyici teknolojisi uyguladı, *katmanlı derleme*, bir opt-in özelliği olarak.</span><span class="sxs-lookup"><span data-stu-id="acc9d-130">In .NET Core 2.1, the JIT compiler implemented a new compiler technology, *tiered compilation*, as an opt-in feature.</span></span> <span data-ttu-id="acc9d-131">Katmanlı derlemenin amacı geliştirilmiş performanstır.</span><span class="sxs-lookup"><span data-stu-id="acc9d-131">The goal of tiered compilation is improved performance.</span></span> <span data-ttu-id="acc9d-132">JIT derleyicisi tarafından gerçekleştirilen önemli görevlerden biri kod yürütmeyi en iyi duruma getirmektir.</span><span class="sxs-lookup"><span data-stu-id="acc9d-132">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="acc9d-133">Ancak az kullanılan kod yolları için derleyici, en iyi duruma getirilmemiş kodu yürütme için çalışma süresiharcadığından daha fazla zaman geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="acc9d-133">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends executing unoptimized code.</span></span> <span data-ttu-id="acc9d-134">Katmanlı derleme JIT derlemesinde iki aşama yı tanıtır:</span><span class="sxs-lookup"><span data-stu-id="acc9d-134">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="acc9d-135">Kodu mümkün olduğunca çabuk üreten **birinci katman.**</span><span class="sxs-lookup"><span data-stu-id="acc9d-135">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="acc9d-136">Sık sık yürütülen bu yöntemler için en iyi duruma getirilmiş kod üreten ikinci bir **katman.**</span><span class="sxs-lookup"><span data-stu-id="acc9d-136">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="acc9d-137">İkinci derleme katmanı, gelişmiş performans için paralel olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="acc9d-137">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="acc9d-138">Katmanlı derlemeden kaynaklanabilecek performans iyileştirmesi hakkında bilgi [için](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/)bkz.</span><span class="sxs-lookup"><span data-stu-id="acc9d-138">For information on the performance improvement that can result from tiered compilation, see [Announcing .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span></span>

<span data-ttu-id="acc9d-139">.NET Core 2.2 Preview 2'de katmanlı derleme varsayılan olarak etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="acc9d-139">In .NET Core 2.2 Preview 2, tiered compilation was enabled by default.</span></span> <span data-ttu-id="acc9d-140">Ancak, varsayılan olarak katmanlı derlemeyi etkinleştirmeye hala hazır olmadığımıza karar verdik.</span><span class="sxs-lookup"><span data-stu-id="acc9d-140">However, we've decided that we are still not ready to enable tiered compilation by default.</span></span> <span data-ttu-id="acc9d-141">Yani .NET Core 2.2'de katmanlı derleme bir tercih özelliği olmaya devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="acc9d-141">So in .NET Core 2.2, tiered compilation continues to be an opt-in feature.</span></span> <span data-ttu-id="acc9d-142">Katmanlı derlemeyi seçme hakkında daha fazla bilgi için [,.NET Core 2.1'deki yeniliklerdeki](dotnet-core-2-1.md) [Jit derleyici geliştirmelerine](dotnet-core-2-1.md#jit-compiler-improvements) bakın.</span><span class="sxs-lookup"><span data-stu-id="acc9d-142">For information on opting in to tiered compilation, see [Jit compiler improvements](dotnet-core-2-1.md#jit-compiler-improvements) in [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span></span>

## <a name="runtime"></a><span data-ttu-id="acc9d-143">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="acc9d-143">Runtime</span></span>

<span data-ttu-id="acc9d-144">**Ana yöntemi yürütmeden önce kod enjekte etme**</span><span class="sxs-lookup"><span data-stu-id="acc9d-144">**Injecting code prior to executing the Main method**</span></span>

<span data-ttu-id="acc9d-145">.NET Core 2.2 ile başlayarak, bir uygulamanın Ana yöntemini çalıştırmadan önce kod enjekte etmek için bir başlangıç kancası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc9d-145">Starting with .NET Core 2.2, you can use a startup hook to inject code prior to running an application's Main method.</span></span> <span data-ttu-id="acc9d-146">Başlangıç kancaları, bir ana bilgisayar için uygulamayı yeniden derlemeye veya değiştirmeye gerek kalmadan dağıtıldıktan sonra uygulamaların davranışını özelleştirmesini mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="acc9d-146">Startup hooks make it possible for a host to customize the behavior of applications after they have been deployed without needing to recompile or change the application.</span></span>

<span data-ttu-id="acc9d-147">Barındırma sağlayıcılarının, ana giriş noktasının yük davranışını etkileyebilecek davranışlar da dahil olmak üzere <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> özel yapılandırma ve ilke tanımlamasını bekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="acc9d-147">We expect hosting providers to define custom configuration and policy, including settings that potentially influence the load behavior of the main entry point, such as the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> behavior.</span></span> <span data-ttu-id="acc9d-148">Kanca, izleme veya telemetri enjeksiyonu kurmak, kullanım için geri aramalar ayarlamak veya çevreye bağlı diğer davranışları tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="acc9d-148">The hook can be used to set up tracing or telemetry injection, to set up callbacks for handling, or to define other environment-dependent behavior.</span></span> <span data-ttu-id="acc9d-149">Kanca giriş noktasından ayrıdır, böylece kullanıcı kodunun değiştirilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="acc9d-149">The hook is separate from the entry point, so that user code doesn't need to be modified.</span></span>

<span data-ttu-id="acc9d-150">Daha fazla bilgi için [Ana Bilgisayar başlatma kancası'na](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="acc9d-150">See [Host startup hook](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="acc9d-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acc9d-151">See also</span></span>

- [<span data-ttu-id="acc9d-152">​.NET Core 3.1’deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="acc9d-152">What's new in .NET Core 3.1</span></span>](dotnet-core-3-1.md)
- [<span data-ttu-id="acc9d-153">ASP.NET Core 2.2'deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="acc9d-153">What's new in ASP.NET Core 2.2</span></span>](/aspnet/core/release-notes/aspnetcore-2.2)
- [<span data-ttu-id="acc9d-154">EF Core 2.2'deki yeni özellikler</span><span class="sxs-lookup"><span data-stu-id="acc9d-154">New features in EF Core 2.2</span></span>](/ef/core/what-is-new/ef-core-2.2)
