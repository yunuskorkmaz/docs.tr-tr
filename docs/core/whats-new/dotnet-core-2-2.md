---
title: .NET Core 2.2 içinde yenilikler nelerdir?
description: .NET Core 2.2 içinde bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.date: 12/04/2018
ms.openlocfilehash: 058e7ee1dc834ff23a9a4aa191f7eaeb1016375c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679783"
---
# <a name="whats-new-in-net-core-22"></a><span data-ttu-id="c2d89-103">.NET Core 2.2 içinde yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="c2d89-103">What's new in .NET Core 2.2</span></span>

<span data-ttu-id="c2d89-104">.NET core 2.2 uygulama dağıtımı, çalışma zamanı Hizmetleri için olay işleme, Azure SQL veritabanları, JIT Derleyici performans ve kod ekleme yürütülmeden önce kimlik doğrulaması geliştirmeleri içerir `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2d89-104">.NET Core 2.2 includes enhancements in application deployment, event handling for runtime services, authentication to Azure SQL databases, JIT compiler performance, and code injection prior to the execution of the `Main` method.</span></span>

## <a name="new-deployment-mode"></a><span data-ttu-id="c2d89-105">Yeni bir dağıtım modu</span><span class="sxs-lookup"><span data-stu-id="c2d89-105">New deployment mode</span></span>

<span data-ttu-id="c2d89-106">Dağıtabileceğiniz .NET Core 2.2 ile başlayarak, [framework bağımlı yürütülebilir dosyaları](../deploying/index.md#framework-dependent-executables-fde), hangi **.exe** yerine dosyaları **.dll** dosyaları.</span><span class="sxs-lookup"><span data-stu-id="c2d89-106">Starting with .NET Core 2.2, you can deploy [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde), which are **.exe** files instead of **.dll** files.</span></span> <span data-ttu-id="c2d89-107">Framework bağımlı dağıtımları, framework bağımlı işlevsel olarak benzer yürütülebilir dosyalar (FDE), yine de bir paylaşılan sistem genelinde sürümünü çalıştırmak için .NET Core varlığını temel kullanır.</span><span class="sxs-lookup"><span data-stu-id="c2d89-107">Functionally similar to framework-dependent deployments, framework-dependent executables (FDE) still rely on the presence of a shared system-wide version of .NET Core to run.</span></span> <span data-ttu-id="c2d89-108">Uygulamanızı, yalnızca kodunuzu ve üçüncü taraf bağımlılıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="c2d89-108">Your app contains only your code and any third-party dependencies.</span></span> <span data-ttu-id="c2d89-109">Framework bağımlı dağıtımları FDEs platforma özgüdür.</span><span class="sxs-lookup"><span data-stu-id="c2d89-109">Unlike framework-dependent deployments, FDEs are platform-specific.</span></span>

<span data-ttu-id="c2d89-110">Bu yeni bir dağıtım modu doğrudan çağırmadan uygulamanızı çalıştırabilir anlamına gelir. bir kitaplık yerine bir yürütülebilir dosya oluşturma, farklı avantajına sahiptir `dotnet` ilk.</span><span class="sxs-lookup"><span data-stu-id="c2d89-110">This new deployment mode has the distinct advantage of building an executable instead of a library, which means you can run your app directly without invoking `dotnet` first.</span></span>

## <a name="core"></a><span data-ttu-id="c2d89-111">Çekirdek</span><span class="sxs-lookup"><span data-stu-id="c2d89-111">Core</span></span>

<span data-ttu-id="c2d89-112">**Çalışma zamanı Hizmetleri olayları işleme**</span><span class="sxs-lookup"><span data-stu-id="c2d89-112">**Handling events in runtime services**</span></span>

<span data-ttu-id="c2d89-113">Genellikle, GC, JIT ve iş parçacığı havuzu, bunların uygulamanızı nasıl etkilediği anlamak için gibi çalışma zamanı Hizmetleri, uygulamanızın kullanımını izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2d89-113">You may often want to monitor your application's use of runtime services, such as the GC, JIT, and ThreadPool, to understand how they impact your application.</span></span><span data-ttu-id="c2d89-114"> Windows sistemlerde, bu genellikle geçerli işlem ETW olaylarını izleme tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c2d89-114"> On Windows systems, this is commonly done by monitoring the ETW events of the current process.</span></span><span data-ttu-id="c2d89-115"> Bu da çalışmaya devam ederken, her zaman düşük ayrıcalıklı bir ortamda veya Linux veya macOS üzerinde çalıştırıyorsanız, ETW kullanmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="c2d89-115"> While this continues to work well, it's not always possible to use ETW if you're running in a low-privilege environment or on Linux or macOS.</span></span>  

<span data-ttu-id="c2d89-116">.NET Core 2.2 ile başlayarak, CoreCLR olayları artık kullanarak tüketilebilir <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithtype> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c2d89-116">Starting with .NET Core 2.2, CoreCLR events can now be consumed using the <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithtype> class.</span></span> <span data-ttu-id="c2d89-117">Bu olaylar, GC, JIT, iş parçacığı havuzu ve birlikte çalışabilirlik gibi çalışma zamanı Hizmetleri davranışını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c2d89-117">These events describe the behavior of such runtime services as GC, JIT, ThreadPool, and interop.</span></span> <span data-ttu-id="c2d89-118">Bu bölümleri aynı olaylardır CoreCLR ETW sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c2d89-118">These are the same events that parts of the CoreCLR ETW provider.</span></span><span data-ttu-id="c2d89-119">  Bu olayları kullanan veya bir telemetri toplama hizmete göndermek aktarım mekanizması kullanmak uygulamalara izin verir.</span><span class="sxs-lookup"><span data-stu-id="c2d89-119">  This allows for applications to consume these events or use a transport mechanism to send them to a telemetry aggregation service.</span></span> <span data-ttu-id="c2d89-120">Aşağıdaki kod örneği olaylara abone olma görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c2d89-120">You can see how to subscribe to events in the following code sample:</span></span>

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

<span data-ttu-id="c2d89-121">Ayrıca, aşağıdaki iki özelliği .NET Core 2.2 ekler <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> ETW olayları hakkında ek bilgi sağlamak için sınıfı:</span><span class="sxs-lookup"><span data-stu-id="c2d89-121">In addition, .NET Core 2.2 adds the following two properties to the <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> class to provide additional information about ETW events:</span></span>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a><span data-ttu-id="c2d89-122">Veri</span><span class="sxs-lookup"><span data-stu-id="c2d89-122">Data</span></span>

<span data-ttu-id="c2d89-123">**Azure SQL veritabanlarına SqlConnection.AccessToken özelliği ile AAD kimlik doğrulaması**</span><span class="sxs-lookup"><span data-stu-id="c2d89-123">**AAD authentication to Azure SQL databases with the SqlConnection.AccessToken property**</span></span>

<span data-ttu-id="c2d89-124">.NET Core 2.2 ile başlayarak, Azure Active Directory tarafından verilen bir erişim belirteci bir Azure SQL veritabanında kimlik doğrulaması için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2d89-124">Starting with .NET Core 2.2, an access token issued by Azure Active Directory can be used to authenticate to an Azure SQL database.</span></span> <span data-ttu-id="c2d89-125">Erişim belirteçleri desteklemek için <xref:System.Data.SqlClient.SqlConnection.AccessToken> özelliği eklendi <xref:System.Data.SqlClient.SqlConnection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c2d89-125">To support access tokens, the <xref:System.Data.SqlClient.SqlConnection.AccessToken> property has been added to the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="c2d89-126">AAD kimlik doğrulaması yararlanmak için 4.6 sürümünü System.Data.SqlClient NuGet paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="c2d89-126">To take advantage of AAD authentication, download version 4.6 of the System.Data.SqlClient NuGet package.</span></span> <span data-ttu-id="c2d89-127">Bu özelliği kullanmak için erişim belirteci değerini kullanarak elde edebilirsiniz [.NET için Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) bulunan [ `Microsoft.IdentityModel.Clients.ActiveDirectory` ](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="c2d89-127">In order to use the feature, you can obtain the access token value using the [Active Directory Authentication Library for .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contained in the [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet package.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="c2d89-128">JIT Derleyici iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c2d89-128">JIT compiler improvements</span></span>

<span data-ttu-id="c2d89-129">**Katmanlı derleme Tercihli özellik kalır.**</span><span class="sxs-lookup"><span data-stu-id="c2d89-129">**Tiered compilation remains an opt-in feature**</span></span>

<span data-ttu-id="c2d89-130">.NET Core 2.1 içinde yeni bir derleyici teknoloji JIT derleyicisi uygulanan *katmanlı derleme*, katılım özelliği olarak.</span><span class="sxs-lookup"><span data-stu-id="c2d89-130">In .NET Core 2.1, the JIT compiler implemented a new compiler technology, *tiered compilation*, as an opt-in feature.</span></span> <span data-ttu-id="c2d89-131">Katmanlı derleme performansı hedeftir.</span><span class="sxs-lookup"><span data-stu-id="c2d89-131">The goal of tiered compilation is improved performance.</span></span> <span data-ttu-id="c2d89-132">JIT derleyicisi tarafından gerçekleştirilen önemli görevlerinden birini ve kod yürütme en iyi duruma getiriyor.</span><span class="sxs-lookup"><span data-stu-id="c2d89-132">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="c2d89-133">Az kullanılan kodu yolları için ancak derleyici kodu çalışma zamanı iyileştirilmemiş kod yürütmek için harcadığı daha iyileştirme daha fazla zaman harcayabilir.</span><span class="sxs-lookup"><span data-stu-id="c2d89-133">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends executing unoptimized code.</span></span> <span data-ttu-id="c2d89-134">Katmanlı bir derleme JIT derlemesi iki aşamada sunar:</span><span class="sxs-lookup"><span data-stu-id="c2d89-134">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="c2d89-135">A **ilk katman**, mümkün olan en kısa sürede kod oluşturduğu.</span><span class="sxs-lookup"><span data-stu-id="c2d89-135">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="c2d89-136">A **ikinci katman**, oluşturduğu kodu sık yürütülen bu yöntemleri için en iyi duruma getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="c2d89-136">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="c2d89-137">Derleme, ikinci katman, Gelişmiş performans için paralel gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c2d89-137">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="c2d89-138">Katmanlı derlemeden sonuçlanabilir performans geliştirmesi hakkında daha fazla bilgi için bkz: [.NET Core 2.2 Önizleme 2 Duyurusu](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="c2d89-138">For information on the performance improvement that can result from tiered compilation, see [Announcing .NET Core 2.2 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span></span> 

<span data-ttu-id="c2d89-139">.NET Core 2.2 Preview 2'deki katmanlı derleme varsayılan olarak etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="c2d89-139">In .NET Core 2.2 Preview 2, tiered compilation was enabled by default.</span></span> <span data-ttu-id="c2d89-140">Ancak biz katmanlı derleme varsayılan olarak etkinleştirmek hala hazır değil duyuyoruz karar verdiniz.</span><span class="sxs-lookup"><span data-stu-id="c2d89-140">However, we've decided that we are still not ready to enable tiered compilation by default.</span></span> <span data-ttu-id="c2d89-141">Bu nedenle .NET Core 2.2 içinde katmanlı derleme Tercihli özellik olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="c2d89-141">So in .NET Core 2.2, tiered compilation continues to be an opt-in feature.</span></span> <span data-ttu-id="c2d89-142">Seçim için katmanlı derleme hakkında daha fazla bilgi için bkz: [JIT Derleyici iyileştirmeleri](dotnet-core-2-1.md#jit-compiler-improvements) içinde [.NET Core 2.1 yenilikler](dotnet-core-2-1.md).</span><span class="sxs-lookup"><span data-stu-id="c2d89-142">For information on opting in to tiered compilation, see [Jit compiler improvements](dotnet-core-2-1.md#jit-compiler-improvements) in [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span></span>

## <a name="runtime"></a><span data-ttu-id="c2d89-143">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="c2d89-143">Runtime</span></span>

<span data-ttu-id="c2d89-144">**Main yöntemine yürütmeden önce kod ekleme**</span><span class="sxs-lookup"><span data-stu-id="c2d89-144">**Injecting code prior to executing the Main method**</span></span>

<span data-ttu-id="c2d89-145">.NET Core 2.2 ile başlayarak, bir uygulamanın ana yöntemi çalıştırılmadan önce kod için bir başlangıç kanca kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2d89-145">Starting with .NET Core 2.2, you can use a startup hook to inject code prior to running an application's Main method.</span></span> <span data-ttu-id="c2d89-146">Başlangıç kancaları yeniden derleyin veya uygulama dağıtmaya gerek kalmadan dağıtıldıktan sonra uygulamalarının davranışını özelleştirmek bir konak olun.</span><span class="sxs-lookup"><span data-stu-id="c2d89-146">Startup hooks make it possible for a host to customize the behavior of applications after they have been deployed without needing to recompile or change the application.</span></span>

<span data-ttu-id="c2d89-147">Özel yapılandırma ve potansiyel olarak gibi uygulamanın ana girdi noktası yükleme davranışını etkileyen ayarları dahil olmak üzere ilke tanımlamak için barındırma sağlayıcılarının bekliyoruz <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> davranışı.</span><span class="sxs-lookup"><span data-stu-id="c2d89-147">We expect hosting providers to define custom configuration and policy, including settings that potentially influence the load behavior of the main entry point, such as the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> behavior.</span></span> <span data-ttu-id="c2d89-148">Kanca geri çağırmaları işlemek için ayarlama veya tanımlamak diğer ortam ayara bağlı davranışı için izleme veya telemetri ekleme ayarlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2d89-148">The hook can be used to set up tracing or telemetry injection, to set up callbacks for handling, or to define other environment-dependent behavior.</span></span> <span data-ttu-id="c2d89-149">Kanca giriş noktasından ayrı, böylelikle kullanıcı kodunun değiştirilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c2d89-149">The hook is separate from the entry point, so that user code doesn't need to be modified.</span></span>

<span data-ttu-id="c2d89-150">Bkz: [konak başlangıç kanca](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="c2d89-150">See [Host startup hook](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2d89-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2d89-151">See also</span></span>

- [<span data-ttu-id="c2d89-152">​.NET Core'daki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="c2d89-152">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="c2d89-153">ASP.NET Core 2.2 içinde yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="c2d89-153">What's new in ASP.NET Core 2.2</span></span>](/aspnet/core/release-notes/aspnetcore-2.2)
- [<span data-ttu-id="c2d89-154">EF Core 2.2 yeni özellikler</span><span class="sxs-lookup"><span data-stu-id="c2d89-154">New features in EF Core 2.2</span></span>](/ef/core/what-is-new/ef-core-2.2)
