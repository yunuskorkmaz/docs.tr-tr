---
title: ​.NET Core 2.2’deki yenilikler
description: .NET Core 2,2 ' de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: 917b51e0cf36cca45135fda4a084eb2bca62e835
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100687"
---
# <a name="whats-new-in-net-core-22"></a><span data-ttu-id="fd561-103">​.NET Core 2.2’deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="fd561-103">What's new in .NET Core 2.2</span></span>

<span data-ttu-id="fd561-104">.NET Core 2,2, uygulama dağıtımında geliştirmeler, çalışma zamanı Hizmetleri için olay işleme, Azure SQL veritabanlarında kimlik doğrulaması, JıT derleyicisi performansı ve `Main` yönteminin yürütülmesinden önce kod ekleme geliştirmeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fd561-104">.NET Core 2.2 includes enhancements in application deployment, event handling for runtime services, authentication to Azure SQL databases, JIT compiler performance, and code injection prior to the execution of the `Main` method.</span></span>

## <a name="new-deployment-mode"></a><span data-ttu-id="fd561-105">Yeni dağıtım modu</span><span class="sxs-lookup"><span data-stu-id="fd561-105">New deployment mode</span></span>

<span data-ttu-id="fd561-106">.NET Core 2,2 ile başlayarak,. **DLL** dosyaları yerine **. exe** dosyaları olan [çerçeveye bağımlı yürütülebilir](../deploying/index.md#framework-dependent-executables-fde)dosyaları dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd561-106">Starting with .NET Core 2.2, you can deploy [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde), which are **.exe** files instead of **.dll** files.</span></span> <span data-ttu-id="fd561-107">İşleve bağımlı dağıtımlara benzer şekilde, çerçeveye bağımlı yürütülebilir dosyalar (FDE), .NET Core 'un paylaşılan sistem genelindeki bir sürümünün çalışmasına de dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd561-107">Functionally similar to framework-dependent deployments, framework-dependent executables (FDE) still rely on the presence of a shared system-wide version of .NET Core to run.</span></span> <span data-ttu-id="fd561-108">Uygulamanız yalnızca kendi kodunuzu ve üçüncü taraf bağımlılıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="fd561-108">Your app contains only your code and any third-party dependencies.</span></span> <span data-ttu-id="fd561-109">Çerçeveye bağımlı dağıtımlardan farklı olarak, FDEs platforma özgüdür.</span><span class="sxs-lookup"><span data-stu-id="fd561-109">Unlike framework-dependent deployments, FDEs are platform-specific.</span></span>

<span data-ttu-id="fd561-110">Bu yeni dağıtım modu, bir kitaplık yerine yürütülebilir bir dosya oluşturmanın farklı avantajına sahiptir. Bu, uygulamanızı öncelikle `dotnet` çağırmadan doğrudan çalıştırabilmeniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fd561-110">This new deployment mode has the distinct advantage of building an executable instead of a library, which means you can run your app directly without invoking `dotnet` first.</span></span>

## <a name="core"></a><span data-ttu-id="fd561-111">Çekirdek</span><span class="sxs-lookup"><span data-stu-id="fd561-111">Core</span></span>

<span data-ttu-id="fd561-112">**Çalışma zamanı hizmetlerindeki olayları işleme**</span><span class="sxs-lookup"><span data-stu-id="fd561-112">**Handling events in runtime services**</span></span>

<span data-ttu-id="fd561-113">Uygulamanızı nasıl etkileyeceğini anlamak için, uygulamanızın GC, JıT ve ThreadPool gibi çalışma zamanı hizmetlerinin kullanımını izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd561-113">You may often want to monitor your application's use of runtime services, such as the GC, JIT, and ThreadPool, to understand how they impact your application.</span></span><span data-ttu-id="fd561-114"> Windows sistemlerinde, bu genellikle geçerli işlemin ETW olayları izlenerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="fd561-114"> On Windows systems, this is commonly done by monitoring the ETW events of the current process.</span></span><span data-ttu-id="fd561-115"> Bu, sorunsuz çalışmaya devam ederken, düşük ayrıcalıklı bir ortamda veya Linux veya macOS 'ta çalışıyorsanız ETW 'yi kullanmak her zaman mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="fd561-115"> While this continues to work well, it's not always possible to use ETW if you're running in a low-privilege environment or on Linux or macOS.</span></span> 

<span data-ttu-id="fd561-116">.NET Core 2,2 ile başlayarak CoreCLR olayları artık <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> sınıfı kullanılarak tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="fd561-116">Starting with .NET Core 2.2, CoreCLR events can now be consumed using the <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="fd561-117">Bu olaylar, bu tür çalışma zamanı hizmetlerinin GC, JıT, ThreadPool ve birlikte çalışma olarak davranışını anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd561-117">These events describe the behavior of such runtime services as GC, JIT, ThreadPool, and interop.</span></span> <span data-ttu-id="fd561-118">Bunlar CoreCLR ETW sağlayıcısı 'nın bir parçası olarak sunulan olaylardır.</span><span class="sxs-lookup"><span data-stu-id="fd561-118">These are the same events that are exposed as part of the CoreCLR ETW provider.</span></span><span data-ttu-id="fd561-119">  Bu, uygulamaların bu olayları kullanmasına veya bir telemetri toplama hizmetine göndermek için bir taşıma mekanizması kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="fd561-119">  This allows for applications to consume these events or use a transport mechanism to send them to a telemetry aggregation service.</span></span> <span data-ttu-id="fd561-120">Aşağıdaki kod örneğinde olaylara nasıl abone olunacağına bakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fd561-120">You can see how to subscribe to events in the following code sample:</span></span>

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

<span data-ttu-id="fd561-121">Ayrıca, .NET Core 2,2, ETW olayları hakkında ek bilgi sağlamak için <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> sınıfına aşağıdaki iki özelliği ekler:</span><span class="sxs-lookup"><span data-stu-id="fd561-121">In addition, .NET Core 2.2 adds the following two properties to the <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> class to provide additional information about ETW events:</span></span>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a><span data-ttu-id="fd561-122">Veri</span><span class="sxs-lookup"><span data-stu-id="fd561-122">Data</span></span>

<span data-ttu-id="fd561-123">**SqlConnection. AccessToken özelliği ile Azure SQL veritabanlarında AAD kimlik doğrulaması**</span><span class="sxs-lookup"><span data-stu-id="fd561-123">**AAD authentication to Azure SQL databases with the SqlConnection.AccessToken property**</span></span>

<span data-ttu-id="fd561-124">.NET Core 2,2 ile başlayarak, Azure Active Directory tarafından verilen bir erişim belirteci, bir Azure SQL veritabanında kimlik doğrulaması yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fd561-124">Starting with .NET Core 2.2, an access token issued by Azure Active Directory can be used to authenticate to an Azure SQL database.</span></span> <span data-ttu-id="fd561-125">Erişim belirteçlerini desteklemek için, <xref:System.Data.SqlClient.SqlConnection.AccessToken> özelliği <xref:System.Data.SqlClient.SqlConnection> sınıfına eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="fd561-125">To support access tokens, the <xref:System.Data.SqlClient.SqlConnection.AccessToken> property has been added to the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="fd561-126">AAD kimlik doğrulamasının avantajlarından yararlanmak için System. Data. SqlClient NuGet paketinin 4,6 sürümünü indirin.</span><span class="sxs-lookup"><span data-stu-id="fd561-126">To take advantage of AAD authentication, download version 4.6 of the System.Data.SqlClient NuGet package.</span></span> <span data-ttu-id="fd561-127">Özelliğini kullanabilmeniz için, [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet paketinde bulunan [.NET için Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) erişim belirteci değerini elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd561-127">In order to use the feature, you can obtain the access token value using the [Active Directory Authentication Library for .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contained in the [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet package.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="fd561-128">JıT derleyicisi geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="fd561-128">JIT compiler improvements</span></span>

<span data-ttu-id="fd561-129">**Katmanlı derleme bir katılım özelliği kalır**</span><span class="sxs-lookup"><span data-stu-id="fd561-129">**Tiered compilation remains an opt-in feature**</span></span>

<span data-ttu-id="fd561-130">.NET Core 2,1 ' de JıT derleyicisi, bir katılım özelliği olarak yeni bir derleyici teknolojisi, *katmanlı derleme*uyguladık.</span><span class="sxs-lookup"><span data-stu-id="fd561-130">In .NET Core 2.1, the JIT compiler implemented a new compiler technology, *tiered compilation*, as an opt-in feature.</span></span> <span data-ttu-id="fd561-131">Katmanlı derlemenin amacı performansı artırmaktır.</span><span class="sxs-lookup"><span data-stu-id="fd561-131">The goal of tiered compilation is improved performance.</span></span> <span data-ttu-id="fd561-132">JıT derleyicisi tarafından gerçekleştirilen önemli görevlerden biri, kod yürütmeyi iyileştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="fd561-132">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="fd561-133">Ancak, daha az kullanılan kod yolları için, derleyici en iyi duruma getirilmiş kodu yürütme çalışma zamanından daha fazla zaman harcayabilir.</span><span class="sxs-lookup"><span data-stu-id="fd561-133">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends executing unoptimized code.</span></span> <span data-ttu-id="fd561-134">Katmanlı derleme JıT derlemesinde iki aşama sunar:</span><span class="sxs-lookup"><span data-stu-id="fd561-134">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="fd561-135">Mümkün olduğunca hızlı bir şekilde kod üreten **ilk katman**.</span><span class="sxs-lookup"><span data-stu-id="fd561-135">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="fd561-136">Sık çalıştırılan yöntemler için iyileştirilmiş kod üreten **ikinci bir katman**.</span><span class="sxs-lookup"><span data-stu-id="fd561-136">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="fd561-137">İkinci derleme katmanı, gelişmiş performans için paralel olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fd561-137">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="fd561-138">Katmanlı derlemeden kaynaklanan performans iyileştirmesi hakkında daha fazla bilgi için bkz. [.NET Core 2,2 Preview 2 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="fd561-138">For information on the performance improvement that can result from tiered compilation, see [Announcing .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span></span>

<span data-ttu-id="fd561-139">.NET Core 2,2 Preview 2 ' de katmanlı derleme varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fd561-139">In .NET Core 2.2 Preview 2, tiered compilation was enabled by default.</span></span> <span data-ttu-id="fd561-140">Ancak, varsayılan olarak katmanlı derlemeyi etkinleştirmeye hazır olmaya devam ediyoruz.</span><span class="sxs-lookup"><span data-stu-id="fd561-140">However, we've decided that we are still not ready to enable tiered compilation by default.</span></span> <span data-ttu-id="fd561-141">Bu nedenle, .NET Core 2,2 ' de katmanlı derleme bir kabul etme özelliği olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="fd561-141">So in .NET Core 2.2, tiered compilation continues to be an opt-in feature.</span></span> <span data-ttu-id="fd561-142">Katmanlı derleme ile ilgili daha fazla bilgi için bkz. [.NET Core 2,1 'deki](dotnet-core-2-1.md)Yenilikler bölümünde [JIT derleyicisi geliştirmeleri](dotnet-core-2-1.md#jit-compiler-improvements) .</span><span class="sxs-lookup"><span data-stu-id="fd561-142">For information on opting in to tiered compilation, see [Jit compiler improvements](dotnet-core-2-1.md#jit-compiler-improvements) in [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span></span>

## <a name="runtime"></a><span data-ttu-id="fd561-143">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="fd561-143">Runtime</span></span>

<span data-ttu-id="fd561-144">**Ana yöntemi yürütmeden önce ekleme kodu**</span><span class="sxs-lookup"><span data-stu-id="fd561-144">**Injecting code prior to executing the Main method**</span></span>

<span data-ttu-id="fd561-145">.NET Core 2,2 ile başlayarak, bir uygulamanın ana metodunu çalıştırmadan önce kodu eklemek için bir başlangıç kancası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd561-145">Starting with .NET Core 2.2, you can use a startup hook to inject code prior to running an application's Main method.</span></span> <span data-ttu-id="fd561-146">Başlangıç kancaları, bir konağın uygulamayı yeniden derlemenize veya değiştirmeye gerek kalmadan dağıtıldıktan sonra uygulamaların davranışını özelleştirmesini olanaklı kılar.</span><span class="sxs-lookup"><span data-stu-id="fd561-146">Startup hooks make it possible for a host to customize the behavior of applications after they have been deployed without needing to recompile or change the application.</span></span>

<span data-ttu-id="fd561-147">Ana giriş noktasının, <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> davranışı gibi yük davranışını etkileyebilecek ayarlar da dahil olmak üzere barındırma sağlayıcılarının özel yapılandırma ve ilke tanımlamasına ihtiyacımız vardır.</span><span class="sxs-lookup"><span data-stu-id="fd561-147">We expect hosting providers to define custom configuration and policy, including settings that potentially influence the load behavior of the main entry point, such as the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> behavior.</span></span> <span data-ttu-id="fd561-148">Kanca, izleme veya telemetri ekleme, işleme için geri çağırmaları ayarlama veya ortama bağlı diğer davranışı tanımlama amacıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fd561-148">The hook can be used to set up tracing or telemetry injection, to set up callbacks for handling, or to define other environment-dependent behavior.</span></span> <span data-ttu-id="fd561-149">Kanca giriş noktasından ayrıdır, bu sayede kullanıcı kodunun değiştirilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fd561-149">The hook is separate from the entry point, so that user code doesn't need to be modified.</span></span>

<span data-ttu-id="fd561-150">Daha fazla bilgi için bkz. [konak başlangıç kancası](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) .</span><span class="sxs-lookup"><span data-stu-id="fd561-150">See [Host startup hook](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd561-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd561-151">See also</span></span>

- [<span data-ttu-id="fd561-152">​.NET Core'daki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="fd561-152">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="fd561-153">ASP.NET Core 2,2 ' deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="fd561-153">What's new in ASP.NET Core 2.2</span></span>](/aspnet/core/release-notes/aspnetcore-2.2)
- [<span data-ttu-id="fd561-154">EF Core 2,2 ' deki yeni özellikler</span><span class="sxs-lookup"><span data-stu-id="fd561-154">New features in EF Core 2.2</span></span>](/ef/core/what-is-new/ef-core-2.2)
