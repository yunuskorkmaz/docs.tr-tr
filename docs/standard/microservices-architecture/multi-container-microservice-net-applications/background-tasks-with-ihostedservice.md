---
title: Mikro IHostedService ve BackgroundService sınıfı ile arka plan görevlerini uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro IHostedService ve BackgroundService sınıfı ile arka plan görevlerini uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 79ad437ef809486b3315de223697ac78109556ba
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105907"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="cd520-103">Mikro IHostedService ve BackgroundService sınıfı ile arka plan görevlerini uygulama</span><span class="sxs-lookup"><span data-stu-id="cd520-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="cd520-104">Arka plan görevleri ve zamanlanmış işler, sonuç olarak, bir temel mikro hizmet uygulaması veya uygulama herhangi bir tür uygulamanız gerekebilir bir şey markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="cd520-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="cd520-105">Mikro mimarisi kullanırken, bir tek mikro hizmet işlemi/ihtiyacınız veya bile, tek bir örneğini çalışacağından emin olmak, aşağı/yukarı ölçeklendirebilirsiniz bu arka plan görevleri barındırma için kapsayıcı uygulayabileceğiniz farktır mikro hizmet işlemi/kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="cd520-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="cd520-106">Konak/uygulama/mikro hizmet içinde ana bilgisayar Hizmetleri/mantığı oldukları için bir genel bakış açısından, .NET Core biz görevleri barındırılan hizmetleri, bu tür çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cd520-106">From a generic point of view, in .NET Core we called these type of tasks Hosted Services, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="cd520-107">Bu durumda, barındırılan hizmet yalnızca arka plan görevi mantığı ile bir sınıf anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cd520-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="cd520-108">.NET Core 2.0 itibaren çerçevesini adlı yeni bir arabirim sağlar. <xref:Microsoft.Extensions.Hosting.IHostedService> kolayca barındırılan uygulama hizmetleri için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="cd520-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="cd520-109">Temel web barındırma arka planda çalışan birden fazla arka plan görevleri (barındırılan Hizmetleri) kaydedebilirsiniz veya konağın çalıştığından, aşağıdaki resimde gösterildiği gibi olur.</span><span class="sxs-lookup"><span data-stu-id="cd520-109">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image below.</span></span>

![](./media/image26.png)

<span data-ttu-id="cd520-110">**Şekil 8-25.**</span><span class="sxs-lookup"><span data-stu-id="cd520-110">**Figure 8-25.**</span></span> <span data-ttu-id="cd520-111">Bir konak karşılaştırması WebHost IHostedService kullanma</span><span class="sxs-lookup"><span data-stu-id="cd520-111">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="cd520-112">Arasında yapılan fark Not `WebHost` ve `Host`.</span><span class="sxs-lookup"><span data-stu-id="cd520-112">Note the difference made between `WebHost` and `Host`.</span></span> <span data-ttu-id="cd520-113">A `WebHost` (sınıfı uygulama temel `IWebHost`) kullandığınız HTTP sunucusu özellikleri IF gibi işleme sağlamak için altyapı yapı bir MVC web uygulaması veya Web API hizmet uygulama ASP.NET Core 2. 0 ' olduğu.</span><span class="sxs-lookup"><span data-stu-id="cd520-113">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="cd520-114">ASP.NET Core, bağımlılık ekleme, middlewares INSERT HTTP ardışık düzen, vb. ve bunlar tam olarak kullanmak sağlayarak yeni tüm altyapı güzelliklerine sağlar `IHostedServices` arka plan görevleri için.</span><span class="sxs-lookup"><span data-stu-id="cd520-114">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the HTTP pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="cd520-115">A `Host` (sınıfı uygulama temel `IHost`), ancak, .NET Core 2.1 içinde yeni bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="cd520-115">A `Host` (base class implementing `IHost`), however, is something new in .NET Core 2.1.</span></span> <span data-ttu-id="cd520-116">Temel olarak, bir `Host` ile sahip daha benzer bir altyapı sahip olmanızı sağlar `WebHost` (bağımlılık ekleme, barındırılan hizmetleri, vb.), ancak bu durumda, yalnızca basit ve daha açık bir işlem, MVC için ilgili herhangi bir şeyin barındırmasını istiyorsanız , Web API veya HTTP sunucusu özellikleri.</span><span class="sxs-lookup"><span data-stu-id="cd520-116">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="cd520-117">Bu nedenle, seçebileceğiniz ve ya da barındırılan hizmetler ve başka bir şey işlemek için yalnızca barındırmak için yapılan mikro IHost ile özel bir ana bilgisayar işlemi oluşturmak `IHostedServices`, veya alternatif olarak, mevcut bir ASP.NET Core genişletebilirsiniz `WebHost` , mevcut bir ASP.NET çekirdek Web API veya MVC uygulaması gibi.</span><span class="sxs-lookup"><span data-stu-id="cd520-117">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span> 

<span data-ttu-id="cd520-118">Her iki yaklaşımın Artıları ve eksileri iş ve ölçeklenebilirlik gereksinimlerinize bağlı olarak vardır.</span><span class="sxs-lookup"><span data-stu-id="cd520-118">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="cd520-119">Arka plan görevleri hiçbir şey varsa, alt çizgi temelde olan HTTP kullanması gereken (IWebHost) ve IHost, kullanılabilir olduğunda .NET Core 2.1 ile yapmak için.</span><span class="sxs-lookup"><span data-stu-id="cd520-119">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use and IHost, when available in .NET Core 2.1.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="cd520-120">WebHost veya ana bilgisayar Hizmetleri'ni barındırılan kaydetme</span><span class="sxs-lookup"><span data-stu-id="cd520-120">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="cd520-121">Şimdi ayrıntıya aşağı hakkında daha fazla `IHostedService` kullanım oldukça benzer olduğundan arabirim bir `WebHost` veya bir `Host`.</span><span class="sxs-lookup"><span data-stu-id="cd520-121">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span> 

<span data-ttu-id="cd520-122">SignalR barındırılan hizmetleri kullanarak bir yapı örneğidir ancak siz de gibi daha kolay şeyler için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cd520-122">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

-   <span data-ttu-id="cd520-123">Değişiklikleri arayan bir veritabanı yoklama bir arka plan görevi.</span><span class="sxs-lookup"><span data-stu-id="cd520-123">A background task polling a database looking for changes.</span></span>
-   <span data-ttu-id="cd520-124">Bazı önbellek düzenli aralıklarla güncelleştirme, zamanlanmış bir görev.</span><span class="sxs-lookup"><span data-stu-id="cd520-124">A scheduled task updating some cache periodically.</span></span>
-   <span data-ttu-id="cd520-125">Arka plan iş parçacığında yürütülecek bir görev verir QueueBackgroundWorkItem uygulaması.</span><span class="sxs-lookup"><span data-stu-id="cd520-125">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
-   <span data-ttu-id="cd520-126">Ortak Hizmetleri gibi paylaşırken bir web uygulaması arka planda bir iletiyi kuyruktan iletileri işleme `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="cd520-126">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
-   <span data-ttu-id="cd520-127">Bir arka plan görevi kullanmaya `Task.Run()`.</span><span class="sxs-lookup"><span data-stu-id="cd520-127">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="cd520-128">Ayrıca, üzerinde IHostedService dayalı bir arka plan görevi için bu eylemlerden herhangi birini temelde boşaltabilir.</span><span class="sxs-lookup"><span data-stu-id="cd520-128">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="cd520-129">Bir veya daha çok eklediğiniz şekilde `IHostedServices` içine, `WebHost` veya `Host` onları oluşturan bir ASP.NET Core, standard DI (bağımlılık ekleme) aracılığıyla kaydederek olan `WebHost` (veya bir `Host` .NET Core 2.1 içinde).</span><span class="sxs-lookup"><span data-stu-id="cd520-129">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1).</span></span> <span data-ttu-id="cd520-130">Temel olarak bilinen içinde barındırılan hizmetler kaydetmek zorunda `ConfigureServices()` yöntemi `Startup` olduğu gibi tipik bir ASP.NET WebHost alınan aşağıdaki kod sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cd520-130">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span> 

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

<span data-ttu-id="cd520-131">Bu kod `GracePeriodManagerService` barındırılan hizmet eShopOnContainers içinde sıralama iş mikro gerçek kodundan, yalnızca iki ek örnekler diğer ikisidir.</span><span class="sxs-lookup"><span data-stu-id="cd520-131">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="cd520-132">`IHostedService` Arka plan görev yürütme (ana bilgisayar veya bu mikro) uygulama ömrü koordine.</span><span class="sxs-lookup"><span data-stu-id="cd520-132">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="cd520-133">Uygulama başlar ve bazı normal bir işlem veya uygulama kapatma sırasında temizleme fırsatı görevleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="cd520-133">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="cd520-134">Kullanmadan `IHostedService`, her zaman herhangi bir görev çalıştırmak için bir arka plan iş parçacığı başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd520-134">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="cd520-135">Tam olarak, ne zaman bu iş parçacığı yalnızca Normal temizleme eylemlerini çalıştırmak için Fırsat gerek kalmadan sonlandırıldı uygulamanın kapatma zaman farktır.</span><span class="sxs-lookup"><span data-stu-id="cd520-135">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>


## <a name="the-ihostedservice-interface"></a><span data-ttu-id="cd520-136">IHostedService arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd520-136">The IHostedService interface</span></span>

<span data-ttu-id="cd520-137">Kaydettiğinizde bir `IHostedService`, .NET Core çağıracaktır `StartAsync()` ve `StopAsync()` yöntemleri, `IHostedService` uygulama başlatma sırasında yazın ve sırasıyla durdurun.</span><span class="sxs-lookup"><span data-stu-id="cd520-137">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="cd520-138">Sunucu başlatıldıktan sonra start özellikle denir ve `IApplicationLifetime.ApplicationStarted` tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="cd520-138">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="cd520-139">`IHostedService` .NET Core tanımlandığı gibi aşağıdaki gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="cd520-139">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

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
<span data-ttu-id="cd520-140">Hayal edebildiğiniz gibi IHostedService birden çok uygulamaları oluşturma ve onları kaydetme `ConfigureService()` daha önce gösterildiği gibi dı kapsayıcı yönteme.</span><span class="sxs-lookup"><span data-stu-id="cd520-140">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="cd520-141">Bu barındırılan tüm hizmetleri kullanmaya ve yanı sıra uygulama/mikro hizmet durduruldu.</span><span class="sxs-lookup"><span data-stu-id="cd520-141">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="cd520-142">Bir geliştirici olarak durdurma eylemi veya hizmetlerinizi işlenmesinden sorumludur zaman `StopAsync()` yöntemi, ana bilgisayar tarafından tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="cd520-142">As a developer, you are responsible for handling the stopping action or your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="cd520-143">BackgroundService temel sınıfından türetilen özel barındırılan hizmet sınıfıyla IHostedService uygulama</span><span class="sxs-lookup"><span data-stu-id="cd520-143">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="cd520-144">Şimdi sıfırdan özel barındırılan hizmet sınıfı oluşturmak ve uygulamak `IHostedService`gibi .NET Core 2.0 kullanırken yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd520-144">You could go ahead and create you custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span> 

<span data-ttu-id="cd520-145">Bununla birlikte, çoğu arka plan görevleri iptal belirteçleri yönetimi ve diğer normal işlemler in regard to benzer gereksinimleri gerekeceğinden, .NET Core 2.1, BackgroundService adlı türetilemeyeceğini çok kullanışlı bir Özet temel sınıf sağlama.</span><span class="sxs-lookup"><span data-stu-id="cd520-145">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, .NET Core 2.1 will be providing a very convenient abstract base class you can derive from, named BackgroundService.</span></span>

<span data-ttu-id="cd520-146">Bu sınıf, arka plan görevi ayarlamanız için gereken ana iş sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd520-146">That class provides the main work needed to set up the background task.</span></span> <span data-ttu-id="cd520-147">Okuma ve yazma gerek kalmaması Bu sınıf .NET Core 2.1 Kitaplığı'nda gelecektir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cd520-147">Note that this class will come in the .NET Core 2.1 library so you don’t need to write it.</span></span>

<span data-ttu-id="cd520-148">Ancak, bu yazma süresi itibariyle .NET Core 2.1 yayınlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="cd520-148">However, as of the time of this writing, .NET Core 2.1 has not been released.</span></span> <span data-ttu-id="cd520-149">İle uyumlu olduğundan bu nedenle, .NET Core 2.0 kullanmakta olduğu eShopOnContainers biz yalnızca geçici olarak .NET Core 2.1 açık kaynak deposu (açık kaynak lisans dışındaki tüm özel lisans gerekmez) bu sınıftan ekleme .NET Core 2.0 geçerli IHostedService arabirimi.</span><span class="sxs-lookup"><span data-stu-id="cd520-149">Therefore, in eShopOnContainers which is currently using .NET Core 2.0, we are just temporally incorporating that class from the .NET Core 2.1 open-source repo (no need of any proprietary license other than the open-source license) because it is compatible with the current IHostedService interface in .NET Core 2.0.</span></span> <span data-ttu-id="cd520-150">.NET Core 2.1 yayımlandığında, yalnızca doğru NuGet paketi noktası gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd520-150">When .NET Core 2.1 is released, you’ll just need to point to the right NuGet package.</span></span>

<span data-ttu-id="cd520-151">Sonraki Özet BackgroundService temel sınıf .NET Core 2.1 içinde uygulandığı şekilde kodudur.</span><span class="sxs-lookup"><span data-stu-id="cd520-151">The next code is the abstract BackgroundService base class as implemented in .NET Core 2.1.</span></span>

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

<span data-ttu-id="cd520-152">Önceki Özet temel sınıf, bu devralınan uygulaması sayesinde'den türetilirken uygulamak yeterlidir `ExecuteAsync()` kendi özel yönteminde barındırılan hizmet sınıfı, aşağıdaki gibi sorgulanır eShopOnContainers koddan Basitleştirilmiş bir veritabanı ve tümleştirme olayları olay gerektiğinde yoluna yayımlama.</span><span class="sxs-lookup"><span data-stu-id="cd520-152">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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

                // This eShopOnContainers method is querying a database table 
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

<span data-ttu-id="cd520-153">EShopOnContainers için belirli bu durumda, belirli bir durumu siparişleri arayan bir veritabanı tablosu sorgulanırken bir uygulama yöntemi yürütme ve değişiklikleri uygularken, olay veri yolu (underneath bu olabilir aracılığıyla tümleştirme olaylarını yayımlama RabbitMQ veya Azure Service Bus kullanarak).</span><span class="sxs-lookup"><span data-stu-id="cd520-153">In this specific case for eShopOnContainers, it is executing an application method which is querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span> 

<span data-ttu-id="cd520-154">Elbette, başka iş arka plan görevi, bunun yerine çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="cd520-154">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="cd520-155">Oluştururken bu değeri değiştirebilirsiniz, ancak varsayılan olarak 5 ikinci zaman aşımı ile iptal belirteci ayarlanır, `WebHost` kullanarak `UseShutdownTimeout` uzantısı `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="cd520-155">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="cd520-156">Başka bir deyişle, hizmetimizi 5 daha aniden sonlandırılacak saniye içinde aksi takdirde iptal beklenir.</span><span class="sxs-lookup"><span data-stu-id="cd520-156">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="cd520-157">Aşağıdaki kod bu süre için 10 saniye değiştirme.</span><span class="sxs-lookup"><span data-stu-id="cd520-157">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="cd520-158">Özet sınıf diyagramı</span><span class="sxs-lookup"><span data-stu-id="cd520-158">Summary class diagram</span></span>

<span data-ttu-id="cd520-159">Aşağıdaki resimde 8-26 IHostedServices uygularken söz konusu interfaced ve görsel sınıflarını Özet gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd520-159">The following image 8-26 shows a visual summary of the classes and interfaced involved when implementing IHostedServices.</span></span>
 
![](./media/image27.png)

<span data-ttu-id="cd520-160">**Şekil 8-26.**</span><span class="sxs-lookup"><span data-stu-id="cd520-160">**Figure 8-26.**</span></span> <span data-ttu-id="cd520-161">Birden çok gösteren sınıf diyagramı IHostedService için ilgili sınıfları ve arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cd520-161">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="cd520-162">Dağıtım hakkında önemli noktalar ve paketler</span><span class="sxs-lookup"><span data-stu-id="cd520-162">Deployment considerations and takeaways</span></span>

<span data-ttu-id="cd520-163">ASP.NET Core dağıtma şeklinizi dikkate almak önemlidir `WebHost` veya .NET Core `Host` nihai çözüm etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="cd520-163">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="cd520-164">Örneğin, dağıtırsanız, `WebHost` IIS veya normal bir Azure uygulama hizmeti, ana bilgisayarınız nedeniyle uygulama havuzu dönüştürür kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd520-164">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="cd520-165">Ancak bir orchestrator Kubernetes veya Service Fabric gibi içine bir kapsayıcı olarak ana bilgisayarınız dağıtıyorsanız, ana bilgisayarınız Canlı örneklerini garantili sayısını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd520-165">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="cd520-166">Ayrıca, diğer yaklaşımlar özellikle Azure işlevleri gibi bu senaryoları için yapılan bulutta düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd520-166">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> 

<span data-ttu-id="cd520-167">Ancak için bile bir `WebHost` bir uygulama havuzu dağıtıldı, yeniden veya hala geçerli olacak uygulamanın bellek içi önbellek temizleme gibi senaryo vardır.</span><span class="sxs-lookup"><span data-stu-id="cd520-167">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="cd520-168">`IHostedService` Arabirimi sağlayan bir ASP.NET Core arka plan görevlerini başlatmak için kolay bir yol web uygulamasında (.NET Core 2. 0'da) veya herhangi bir işlem/ana (.NET Core 2.1 ile başlangıç `IHost`).</span><span class="sxs-lookup"><span data-stu-id="cd520-168">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="cd520-169">Kendi ana avantajı konak kapatma sırasında normal iptal edilmesini arka plan görevleri ile temizleme koduna alma fırsattır.</span><span class="sxs-lookup"><span data-stu-id="cd520-169">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>


#### <a name="additional-resources"></a><span data-ttu-id="cd520-170">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="cd520-170">Additional resources</span></span>

-   <span data-ttu-id="cd520-171">**ASP.NET Core/standart 2.0 zamanlanmış bir görev oluşturma**</span><span class="sxs-lookup"><span data-stu-id="cd520-171">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span> 

    [*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   <span data-ttu-id="cd520-172">**ASP.NET Core 2.0 IHostedService uygulama**</span><span class="sxs-lookup"><span data-stu-id="cd520-172">**Implementing IHostedService in ASP.NET Core 2.0**</span></span> 

    [*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   <span data-ttu-id="cd520-173">**ASP.NET Core 2.1 barındırma örnekleri**</span><span class="sxs-lookup"><span data-stu-id="cd520-173">**ASP.NET Core 2.1 Hosting samples**</span></span> 

    [*https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample*](https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample)



>[!div class="step-by-step"]
<span data-ttu-id="cd520-174">[Önceki](test-aspnet-core-services-web-apps.md)
[sonraki](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="cd520-174">[Previous](test-aspnet-core-services-web-apps.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
