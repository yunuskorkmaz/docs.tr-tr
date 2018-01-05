---
title: "Mikro IHostedService ve BackgroundService sınıfı ile arka plan görevlerini uygulama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro IHostedService ve BackgroundService sınıfı ile arka plan görevlerini uygulama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d60a4590682b79a9f8ac57afee09884b7edd1f98
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="8988f-104">Mikro IHostedService ve BackgroundService sınıfı ile arka plan görevlerini uygulama</span><span class="sxs-lookup"><span data-stu-id="8988f-104">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="8988f-105">Arka plan görevleri ve zamanlanmış işler, sonuç olarak, bir temel mikro hizmet uygulaması veya uygulama herhangi bir tür uygulamanız gerekebilir bir şey markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="8988f-105">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="8988f-106">Mikro mimarisi kullanırken, bir tek mikro hizmet işlemi/ihtiyacınız veya bile, tek bir örneğini çalışacağından emin olmak, aşağı/yukarı ölçeklendirebilirsiniz bu arka plan görevleri barındırma için kapsayıcı uygulayabileceğiniz farktır mikro hizmet işlemi/kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="8988f-106">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="8988f-107">Konak/uygulama/mikro hizmet içinde ana bilgisayar Hizmetleri/mantığı oldukları için bir genel bakış açısından, .NET Core biz görevleri barındırılan hizmetleri, bu tür çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8988f-107">From a generic point of view, in .NET Core we called these type of tasks Hosted Services, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="8988f-108">Bu durumda, barındırılan hizmet yalnızca arka plan görevi mantığı ile bir sınıf anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8988f-108">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="8988f-109">.NET Core 2.0 itibaren çerçevesini adlı yeni bir arabirim sağlar. <xref:Microsoft.Extensions.Hosting.IHostedService> kolayca barındırılan uygulama hizmetleri için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="8988f-109">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="8988f-110">Temel web barındırma arka planda çalışan birden fazla arka plan görevleri (barındırılan Hizmetleri) kaydedebilirsiniz veya konağın çalıştığından, aşağıdaki resimde gösterildiği gibi olur.</span><span class="sxs-lookup"><span data-stu-id="8988f-110">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image below.</span></span>

![](./media/image26.png)

<span data-ttu-id="8988f-111">**Şekil 8-25.**</span><span class="sxs-lookup"><span data-stu-id="8988f-111">**Figure 8-25.**</span></span> <span data-ttu-id="8988f-112">Bir konak karşılaştırması WebHost IHostedService kullanma</span><span class="sxs-lookup"><span data-stu-id="8988f-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="8988f-113">Arasında yapılan fark Not `WebHost` ve `Host`.</span><span class="sxs-lookup"><span data-stu-id="8988f-113">Note the difference made between `WebHost` and `Host`.</span></span> <span data-ttu-id="8988f-114">A `WebHost` (sınıfı uygulama temel `IWebHost`) kullandığınız HTTP sunucusu özellikleri IF gibi işleme sağlamak için altyapı yapı bir MVC web uygulaması veya Web API hizmet uygulama ASP.NET Core 2. 0 ' olduğu.</span><span class="sxs-lookup"><span data-stu-id="8988f-114">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="8988f-115">ASP.NET Core, bağımlılık ekleme, middlewares INSERT HTTP ardışık düzen, vb. ve bunlar tam olarak kullanmak sağlayarak yeni tüm altyapı güzelliklerine sağlar `IHostedServices` arka plan görevleri için.</span><span class="sxs-lookup"><span data-stu-id="8988f-115">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the HTTP pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="8988f-116">A `Host` (sınıfı uygulama temel `IHost`), ancak, .NET Core 2.1 içinde yeni bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="8988f-116">A `Host` (base class implementing `IHost`), however, is something new in .NET Core 2.1.</span></span> <span data-ttu-id="8988f-117">Temel olarak, bir `Host` ile sahip daha benzer bir altyapı sahip olmanızı sağlar `WebHost` (bağımlılık ekleme, barındırılan hizmetleri, vb.), ancak bu durumda, yalnızca basit ve daha açık bir işlem, MVC için ilgili herhangi bir şeyin barındırmasını istiyorsanız , Web API veya HTTP sunucusu özellikleri.</span><span class="sxs-lookup"><span data-stu-id="8988f-117">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="8988f-118">Bu nedenle, seçebileceğiniz ve ya da barındırılan hizmetler ve başka bir şey işlemek için yalnızca barındırmak için yapılan mikro IHost ile özel bir ana bilgisayar işlemi oluşturmak `IHostedServices`, veya alternatevely mevcut bir ASP.NET Core genişletme `WebHost` , mevcut bir ASP.NET çekirdek Web API veya MVC uygulaması gibi.</span><span class="sxs-lookup"><span data-stu-id="8988f-118">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatevely extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span> 

<span data-ttu-id="8988f-119">Her iki yaklaşımın Artıları ve eksileri iş ve ölçeklenebilirlik gereksinimlerinize bağlı olarak vardır.</span><span class="sxs-lookup"><span data-stu-id="8988f-119">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="8988f-120">Arka plan görevleri hiçbir şey varsa, alt çizgi temelde olan HTTP kullanması gereken (IWebHost) ve IHost, kullanılabilir olduğunda .NET Core 2.1 ile yapmak için.</span><span class="sxs-lookup"><span data-stu-id="8988f-120">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use and IHost, when available in .NET Core 2.1.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="8988f-121">WebHost veya ana bilgisayar Hizmetleri'ni barındırılan kaydetme</span><span class="sxs-lookup"><span data-stu-id="8988f-121">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="8988f-122">Şimdi ayrıntıya aşağı hakkında daha fazla `IHostedService` kullanım oldukça benzer olduğundan arabirim bir `WebHost` veya bir `Host`.</span><span class="sxs-lookup"><span data-stu-id="8988f-122">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span> 

<span data-ttu-id="8988f-123">SignalR barındırılan hizmetleri kullanarak bir yapı örneğidir ancak siz de gibi daha kolay şeyler için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8988f-123">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

-   <span data-ttu-id="8988f-124">Değişiklikleri arayan bir veritabanı yoklama bir arka plan görevi.</span><span class="sxs-lookup"><span data-stu-id="8988f-124">A background task polling a database looking for changes.</span></span>
-   <span data-ttu-id="8988f-125">Bazı önbellek düzenli aralıklarla güncelleştirme, zamanlanmış bir görev.</span><span class="sxs-lookup"><span data-stu-id="8988f-125">A scheduled task updating some cache periodically.</span></span>
-   <span data-ttu-id="8988f-126">Arka plan iş parçacığında yürütülecek bir görev verir QueueBackgroundWorkItem uygulaması.</span><span class="sxs-lookup"><span data-stu-id="8988f-126">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
-   <span data-ttu-id="8988f-127">Ortak Hizmetleri gibi paylaşırken bir web uygulaması arka planda bir iletiyi kuyruktan iletileri işleme `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="8988f-127">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
-   <span data-ttu-id="8988f-128">Bir arka plan görevi kullanmaya `Task.Run()`.</span><span class="sxs-lookup"><span data-stu-id="8988f-128">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="8988f-129">Ayrıca, üzerinde IHostedService dayalı bir arka plan görevi için bu eylemlerden herhangi birini temelde boşaltabilir.</span><span class="sxs-lookup"><span data-stu-id="8988f-129">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="8988f-130">Bir veya daha çok eklediğiniz şekilde `IHostedServices` içine, `WebHost` veya `Host` onları oluşturan bir ASP.NET Core, standard DI (bağımlılık ekleme) aracılığıyla kaydederek olan `WebHost` (veya bir `Host` .NET Core 2.1 içinde).</span><span class="sxs-lookup"><span data-stu-id="8988f-130">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1).</span></span> <span data-ttu-id="8988f-131">Temel olarak bilinen içinde barındırılan hizmetler kaydetmek zorunda `ConfigureServices()` yöntemi `Startup` olduğu gibi tipik bir ASP.NET WebHost alınan aşağıdaki kod sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8988f-131">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span> 

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{            
    //Other DI registrations;

    // Register Hosted Services
    services.AddSingleton<IHostedService, GracePeriodManagerService>();
    services.AddSingleton<IHostedService, MyHostedServiceB>();
    services.AddSingleton<IHostedService, MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="8988f-132">Bu kod `GracePeriodManagerService` barındırılan hizmet eShopOnContainers içinde sıralama iş mikro gerçek kodundan, yalnızca iki ek örnekler diğer ikisidir.</span><span class="sxs-lookup"><span data-stu-id="8988f-132">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="8988f-133">`IHostedService` Arka plan görev yürütme (ana bilgisayar veya bu mikro) uygulama ömrü koordine.</span><span class="sxs-lookup"><span data-stu-id="8988f-133">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="8988f-134">Uygulama başlar ve bazı normal bir işlem veya uygulama kapatma sırasında temizleme fırsatı görevleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="8988f-134">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="8988f-135">Kullanmadan `IHostedService`, her zaman herhangi bir görev çalıştırmak için bir arka plan iş parçacığı başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8988f-135">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="8988f-136">Tam olarak, ne zaman bu iş parçacığı yalnızca Normal temizleme eylemlerini çalıştırmak için Fırsat gerek kalmadan sonlandırıldı uygulamanın kapatma zaman farktır.</span><span class="sxs-lookup"><span data-stu-id="8988f-136">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>


## <a name="the-ihostedservice-interface"></a><span data-ttu-id="8988f-137">IHostedService arabirimi</span><span class="sxs-lookup"><span data-stu-id="8988f-137">The IHostedService interface</span></span>

<span data-ttu-id="8988f-138">Kaydettiğinizde bir `IHostedService`, .NET Core çağıracaktır `StartAsync()` ve `StopAsync()` yöntemleri, `IHostedService` uygulama başlatma sırasında yazın ve sırasıyla durdurun.</span><span class="sxs-lookup"><span data-stu-id="8988f-138">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="8988f-139">Sunucu başlatıldıktan sonra start özellikle denir ve `IApplicationLifetime.ApplicationStarted` tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="8988f-139">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="8988f-140">`IHostedService` .NET Core tanımlandığı gibi aşağıdaki gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="8988f-140">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

```csharp
namespace Microsoft.Extensions.Hosting
{
    //
    // Summary:
    //     Defines methods for objects that are managed by the host.
    public interface IHostedService
    {
        //
        // Summary:
        // Triggered when the application host is ready to start the service.
        Task StartAsync(CancellationToken cancellationToken);
        //
        // Summary:
        // Triggered when the application host is performing a graceful shutdown.
        Task StopAsync(CancellationToken cancellationToken);
    }
}
```
<span data-ttu-id="8988f-141">Hayal edebildiğiniz gibi IHostedService birden çok uygulamaları oluşturma ve onları kaydetme `ConfigureService()` daha önce gösterildiği gibi dı kapsayıcı yönteme.</span><span class="sxs-lookup"><span data-stu-id="8988f-141">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="8988f-142">Bu barındırılan tüm hizmetleri kullanmaya ve yanı sıra uygulama/mikro hizmet durduruldu.</span><span class="sxs-lookup"><span data-stu-id="8988f-142">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="8988f-143">Bir geliştirici olarak durdurma eylemi veya hizmetlerinizi işlenmesinden sorumludur zaman `StopAsync()` yöntemi, ana bilgisayar tarafından tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="8988f-143">As a developer, you are responsible for handling the stopping action or your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="8988f-144">BackgroundService temel sınıfından türetilen özel barındırılan hizmet sınıfıyla IHostedService uygulama</span><span class="sxs-lookup"><span data-stu-id="8988f-144">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="8988f-145">Şimdi sıfırdan özel barındırılan hizmet sınıfı oluşturmak ve uygulamak `IHostedService`gibi .NET Core 2.0 kullanırken yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8988f-145">You could go ahead and create you custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span> 

<span data-ttu-id="8988f-146">Bununla birlikte, çoğu arka plan görevleri iptal belirteçleri yönetimi ve diğer tipical işlemler in regard to benzer gereksinimleri gerekeceğinden, .NET Core 2.1, BackgroundService adlı türetilemeyeceğini çok kullanışlı bir Özet temel sınıf sağlama.</span><span class="sxs-lookup"><span data-stu-id="8988f-146">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other tipical operations, .NET Core 2.1 will be providing a very convenient abstract base class you can derive from, named BackgroundService.</span></span>

<span data-ttu-id="8988f-147">Bu sınıf, arka plan görevi ayarlamanız için gereken ana iş sağlar.</span><span class="sxs-lookup"><span data-stu-id="8988f-147">That class provides the main work needed to set up the background task.</span></span> <span data-ttu-id="8988f-148">Okuma ve yazma gerek kalmaması Bu sınıf .NET Core 2.1 Kitaplığı'nda gelecektir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8988f-148">Note that this class will come in the .NET Core 2.1 library so you don’t need to write it.</span></span>

<span data-ttu-id="8988f-149">Ancak, bu yazma süresi itibariyle .NET Core 2.1 yayınlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="8988f-149">However, as of the time of this writing, .NET Core 2.1 has not been released.</span></span> <span data-ttu-id="8988f-150">İle uyumlu olduğundan bu nedenle, .NET Core 2.0 kullanmakta olduğu eShopOnContainers biz yalnızca geçici olarak .NET Core 2.1 açık kaynak deposu (açık kaynak lisans dışındaki tüm özel lisans gerekmez) bu sınıftan ekleme .NET Core 2.0 geçerli IHostedService arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8988f-150">Therefore, in eShopOnContainers which is currently using .NET Core 2.0, we are just temporally incorporating that class from the .NET Core 2.1 open-source repo (no need of any proprietary license other than the open-source license) because it is compatible with the current IHostedService interface in .NET Core 2.0.</span></span> <span data-ttu-id="8988f-151">.NET Core 2.1 yayımlandığında, yalnızca doğru NuGet paketi noktası gerekir.</span><span class="sxs-lookup"><span data-stu-id="8988f-151">When .NET Core 2.1 is released, you’ll just need to point to the right NuGet package.</span></span>

<span data-ttu-id="8988f-152">Sonraki Özet BackgroundService temel sınıf .NET Core 2.1 içinde uygulandığı şekilde kodudur.</span><span class="sxs-lookup"><span data-stu-id="8988f-152">The next code is the abstract BackgroundService base class as implemented in .NET Core 2.1.</span></span>

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0. 
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts = 
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it, 
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }
    
    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

<span data-ttu-id="8988f-153">Önceki Özet temel sınıf, bu devralınan uygulaması sayesinde'den türetilirken uygulamak yeterlidir `ExecuteAsync()` kendi özel yönteminde barındırılan hizmet sınıfı, aşağıdaki gibi sorgulanır eShopOnContainers koddan Basitleştirilmiş bir veritabanı ve tümleştirme olayları olay gerektiğinde yoluna yayımlama.</span><span class="sxs-lookup"><span data-stu-id="8988f-153">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

```csharp
public class GracePeriodManagerService : BackgroundService
{        
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
        {
            //Constructor’s parameters validations...       
        }

        protected override async Task ExecuteAsync(CancellationToken stoppingToken)
        {
            _logger.LogDebug($"GracePeriodManagerService is starting.");

            stoppingToken.Register(() => 
                    _logger.LogDebug($" GracePeriod background task is stopping."));

            while (!stoppingToken.IsCancellationRequested)
            {
                _logger.LogDebug($"GracePeriod task doing background work.");

                // This eShopOnContainers method is quering a database table 
                // and publishing events into the Event Bus (RabbitMS / ServiceBus)
                CheckConfirmedGracePeriodOrders();

                await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
            }
            
            _logger.LogDebug($"GracePeriod background task is stopping.");

        }

        protected override async Task StopAsync (CancellationToken stoppingToken)
        {
               // Run your graceful clean-up actions
        }
}
```

<span data-ttu-id="8988f-154">Bu belirli durumda eShopOnContainers için quering görmek bir veritabanı tablosu siparişleri belirli bir durumu ve değişiklikleri uygularken, olay veri yolu (underneath bu olabilir aracılığıyla tümleştirme olaylarını yayımlama olan uygulama yöntemini yürütüyor RabbitMQ veya Azure Service Bus kullanarak).</span><span class="sxs-lookup"><span data-stu-id="8988f-154">In this specific case for eShopOnContainers, it is executing an application method which is quering a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span> 

<span data-ttu-id="8988f-155">Elbette, başka iş arka plan görevi, bunun yerine çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="8988f-155">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="8988f-156">Oluştururken bu değeri değiştirebilirsiniz, ancak varsayılan olarak 5 ikinci zaman aşımı ile iptal belirteci ayarlanır, `WebHost` kullanarak `UseShutdownTimeout` uzantısı `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="8988f-156">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="8988f-157">Başka bir deyişle, hizmetimizi 5 daha aniden sonlandırılacak saniye içinde aksi takdirde iptal beklenir.</span><span class="sxs-lookup"><span data-stu-id="8988f-157">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="8988f-158">Aşağıdaki kod bu süre için 10 saniye değiştirme.</span><span class="sxs-lookup"><span data-stu-id="8988f-158">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="8988f-159">Özet sınıf diyagramı</span><span class="sxs-lookup"><span data-stu-id="8988f-159">Summary class diagram</span></span>

<span data-ttu-id="8988f-160">Aşağıdaki resimde 8-26 IHostedServices uygularken söz konusu interfaced ve görsel sınıflarını Özet gösterir.</span><span class="sxs-lookup"><span data-stu-id="8988f-160">The following image 8-26 shows a visual summary of the classes and interfaced involved when implementing IHostedServices.</span></span>
 
![](./media/image27.png)

<span data-ttu-id="8988f-161">**Şekil 8-26.**</span><span class="sxs-lookup"><span data-stu-id="8988f-161">**Figure 8-26.**</span></span> <span data-ttu-id="8988f-162">Birden çok gösteren sınıf diyagramı IHostedService için ilgili sınıfları ve arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8988f-162">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="8988f-163">Dağıtım hakkında önemli noktalar ve paketler</span><span class="sxs-lookup"><span data-stu-id="8988f-163">Deployment considerations and takeaways</span></span>

<span data-ttu-id="8988f-164">ASP.NET Core dağıtma şeklinizi dikkate almak önemlidir `WebHost` veya .NET Core `Host` nihai çözüm etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="8988f-164">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="8988f-165">Örneğin, dağıtırsanız, `WebHost` IIS veya normal bir Azure uygulama hizmeti, ana bilgisayarınız nedeniyle uygulama havuzu dönüştürür kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="8988f-165">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="8988f-166">Ancak bir orchestrator Kubernetes veya Service Fabric gibi içine bir kapsayıcı olarak ana bilgisayarınız dağıtıyorsanız, ana bilgisayarınız Canlı örneklerini garantili sayısını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8988f-166">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="8988f-167">Ayrıca, diğer yaklaşımlar özellikle Azure işlevleri gibi bu senaryoları için yapılan bulutta düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8988f-167">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> 

<span data-ttu-id="8988f-168">Ancak için bile bir `WebHost` bir uygulama havuzu dağıtıldı, yeniden veya hala geçerli olacak uygulamanın bellek içi önbellek temizleme gibi senaryo vardır.</span><span class="sxs-lookup"><span data-stu-id="8988f-168">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="8988f-169">`IHostedService` Arabirimi sağlayan bir ASP.NET Core arka plan görevlerini başlatmak için kolay bir yol web uygulamasında (.NET Core 2. 0'da) veya herhangi bir işlem/ana (.NET Core 2.1 ile başlangıç `IHost`).</span><span class="sxs-lookup"><span data-stu-id="8988f-169">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="8988f-170">Kendi ana avantajı konak kapatma sırasında normal iptal edilmesini arka plan görevleri ile temizleme koduna alma fırsattır.</span><span class="sxs-lookup"><span data-stu-id="8988f-170">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>


#### <a name="additional-resources"></a><span data-ttu-id="8988f-171">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="8988f-171">Additional resources</span></span>

-   <span data-ttu-id="8988f-172">**ASP.NET Core/standart 2.0 zamanlanmış bir görev oluşturma**</span><span class="sxs-lookup"><span data-stu-id="8988f-172">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span> 

    [<span data-ttu-id="8988f-173">*https://blog.maartenballiauw.be/POST/2017/08/01/Building-a-Scheduled-Cache-Updater-in-ASPNET-Core-2.HTML*</span><span class="sxs-lookup"><span data-stu-id="8988f-173">*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*</span></span>](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   <span data-ttu-id="8988f-174">**ASP.NET Core 2.0 IHostedService uygulama**</span><span class="sxs-lookup"><span data-stu-id="8988f-174">**Implementing IHostedService in ASP.NET Core 2.0**</span></span> 

    [<span data-ttu-id="8988f-175">*https://www.stevejgordon.co.uk/ASP-NET-Core-2-ihostedservice*</span><span class="sxs-lookup"><span data-stu-id="8988f-175">*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*</span></span>](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   <span data-ttu-id="8988f-176">**ASP.NET Core 2.1 barındırma örnekleri**</span><span class="sxs-lookup"><span data-stu-id="8988f-176">**ASP.NET Core 2.1 Hosting samples**</span></span> 

    [<span data-ttu-id="8988f-177">*https://github.com/ASPNET/Hosting/Tree/dev/Samples/GenericHostSample*</span><span class="sxs-lookup"><span data-stu-id="8988f-177">*https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample*</span></span>](https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample)



>[!div class="step-by-step"]
<span data-ttu-id="8988f-178">[Önceki] (test-aspnet-core-services-web-apps.md) [sonraki] (.. /microservice-ddd-cqrs-Patterns/index.MD)</span><span class="sxs-lookup"><span data-stu-id="8988f-178">[Previous] (test-aspnet-core-services-web-apps.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>
