---
title: Ihostedservice ve BackgroundService sınıfıyla mikro hizmetlerde arka plan görevleri uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Mikro hizmetler .NET Core 'da arka plan görevleri uygulamak için ıhostedservice ve BackgroundService kullanmak üzere yeni seçenekleri anlayın.
ms.date: 08/14/2020
ms.openlocfilehash: 4ab215f2196cd2e66b116465c3a582a9846c8066
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88268003"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="bdba2-103">Ihostedservice ve BackgroundService sınıfıyla mikro hizmetlerde arka plan görevleri uygulama</span><span class="sxs-lookup"><span data-stu-id="bdba2-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="bdba2-104">Arka plan görevleri ve zamanlanan işler, mikro hizmetler mimari modelini takip etmeksizin, herhangi bir uygulamada kullanmanız gerekebilecek bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="bdba2-104">Background tasks and scheduled jobs are something you might need to use in any application, whether or not it follows the microservices architecture pattern.</span></span> <span data-ttu-id="bdba2-105">Mikro hizmet mimarisi kullanmanın farkı, arka plan görevini, barındırmak üzere ayrı bir süreç/kapsayıcıda uygulayabileceğiniz için, ihtiyacınız olan temelinde ölçeklendirebilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdba2-105">The difference when using a microservices architecture is that you can implement the background task in a separate process/container for hosting so you can scale it down/up based on your need.</span></span>

<span data-ttu-id="bdba2-106">.NET Core 'da, genel bir bakış noktasından, ana bilgisayar/uygulama/mikro hizmetiniz içinde barındırmanıza yönelik hizmetler/mantık olduklarından, bu tür görevler *barındırılan hizmetler*olarak adlandırdık.</span><span class="sxs-lookup"><span data-stu-id="bdba2-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="bdba2-107">Bu durumda, barındırılan hizmetin arka plan görevi mantığına sahip bir sınıf anlamına geldiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bdba2-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="bdba2-108">.NET Core 2,0 sürümünden itibaren Framework, <xref:Microsoft.Extensions.Hosting.IHostedService> barındırılan Hizmetleri kolayca uygulamanıza yardımcı adlı yeni bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdba2-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="bdba2-109">Temel düşünce, 6-26 görüntüsünde gösterildiği gibi Web ana bilgisayarınız veya ana bilgisayarınız çalışırken arka planda çalışan birden fazla arka plan görevini (barındırılan hizmetler) kaydedebilmeniz için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bdba2-109">The basic idea is that you can register multiple background tasks (hosted services) that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![ASP.NET Core ıwebhost ve .NET Core IHOST karşılaştırması.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

<span data-ttu-id="bdba2-111">**Şekil 6-26**.</span><span class="sxs-lookup"><span data-stu-id="bdba2-111">**Figure 6-26**.</span></span> <span data-ttu-id="bdba2-112">Bir WebHost 'de ıhostedservice kullanma ve bir ana bilgisayar</span><span class="sxs-lookup"><span data-stu-id="bdba2-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="bdba2-113">`IWebHost`Web Apps 'te arka plan işlemlerine yönelik 1. x ve 2. x desteği ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="bdba2-113">ASP.NET Core 1.x and 2.x support `IWebHost` for background processes in web apps.</span></span> <span data-ttu-id="bdba2-114">.NET Core 2,1 ve üzeri sürümleri, `IHost` düz konsol uygulamalarıyla arka plan süreçlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="bdba2-114">.NET Core 2.1 and later versions support `IHost` for background processes with plain console apps.</span></span> <span data-ttu-id="bdba2-115">Ve arasında yapılan farkı dikkate `WebHost` alın `Host` .</span><span class="sxs-lookup"><span data-stu-id="bdba2-115">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="bdba2-116">`WebHost`ASP.NET Core 2,0 ' de bir (temel sınıf uygulayan `IWebHost` ), bir MVC web uygulaması veya Web API hizmeti uygularken, Işlem uygulamanıza http sunucusu özellikleri sağlamak için kullandığınız altyapı yapıtıdır.</span><span class="sxs-lookup"><span data-stu-id="bdba2-116">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as when you're implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="bdba2-117">ASP.NET Core, bağımlılık ekleme, istek ardışık düzeninde middlewares ekleme ve benzer şekilde tüm yeni altyapıyı bir araya getirir.</span><span class="sxs-lookup"><span data-stu-id="bdba2-117">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, and similar.</span></span> <span data-ttu-id="bdba2-118">, `WebHost` `IHostedServices` Arka plan görevleri için bu çok aynısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="bdba2-118">The `WebHost` uses these very same `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="bdba2-119">`Host` `IHost` .Net Core 2,1 ' de bir (temel sınıf uygulayan) tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="bdba2-119">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="bdba2-120">Temel olarak, sahip `Host` olduğunuz kadar benzer bir altyapıya sahip olmanız `WebHost` (bağımlılık ekleme, barındırılan hizmetler vb.), ancak bu durumda, MVC, Web API 'SI veya http sunucu özellikleriyle ilgili hiçbir şey olmadan ana bilgisayar için basit ve daha hafif bir işleme sahip olmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="bdba2-120">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="bdba2-121">Bu nedenle, barındırılan Hizmetleri işlemek için ile özel bir konak oluşturma ve `IHost` başka hiçbir şey yapma (örneğin, yalnızca barındırmak için yapılan bir mikro hizmet) veya var olan bir `IHostedServices` `WebHost` ASP.NET Core Web API 'SI ya da MVC uygulaması gibi mevcut bir ASP.NET Core genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdba2-121">Therefore, you can choose and either create a specialized host-process with `IHost` to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="bdba2-122">Her yaklaşımın iş ve ölçeklenebilirlik gereksinimlerinize bağlı olarak profesyonelleri ve dezavantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="bdba2-122">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="bdba2-123">Arka plan görevleriniz, kullanmanız gereken HTTP () ile hiçbir şey yapmayabilir `IWebHost` `IHost` .</span><span class="sxs-lookup"><span data-stu-id="bdba2-123">The bottom line is basically that if your background tasks have nothing to do with HTTP (`IWebHost`) you should use `IHost`.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="bdba2-124">Barındırılan Hizmetleri WebHost veya ana bilgisayarınıza kaydetme</span><span class="sxs-lookup"><span data-stu-id="bdba2-124">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="bdba2-125">Kullanımı, içinde veya ' de oldukça benzer olduğundan arabirim üzerinde daha fazla ayrıntıya bakalım `IHostedService` `WebHost` `Host` .</span><span class="sxs-lookup"><span data-stu-id="bdba2-125">Let's drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="bdba2-126">SignalR, barındırılan Hizmetleri kullanan bir yapıtın örneğidir, ancak şu gibi daha basit şeyler için de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bdba2-126">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="bdba2-127">Arka plan görevi, değişiklik isteyen bir veritabanını yoklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="bdba2-127">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="bdba2-128">Belirli bir önbelleği düzenli aralıklarla güncelleştiren zamanlanmış bir görev.</span><span class="sxs-lookup"><span data-stu-id="bdba2-128">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="bdba2-129">Bir görevin arka plan iş parçacığında yürütülmesini sağlayan QueueBackgroundWorkItem 'ın bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="bdba2-129">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="bdba2-130">Gibi ortak hizmetleri paylaşırken bir Web uygulamasının arka planında bir ileti kuyruğundan iletileri işleme `ILogger` .</span><span class="sxs-lookup"><span data-stu-id="bdba2-130">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="bdba2-131">İle başlatılan bir arka plan görevi `Task.Run()` .</span><span class="sxs-lookup"><span data-stu-id="bdba2-131">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="bdba2-132">Bu eylemlerin herhangi birini, uygulayan bir arka plan görevine temelde devretmek `IHostedService` .</span><span class="sxs-lookup"><span data-stu-id="bdba2-132">You can basically offload any of those actions to a background task that implements `IHostedService`.</span></span>

<span data-ttu-id="bdba2-133">Veya ' a bir veya daha fazla ekleme yönteminiz, `IHostedServices` `WebHost` bunları bir `Host` <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>   ASP.NET Core genişletme yöntemiyle `WebHost` (veya `Host` .NET Core 2,1 ve üzeri sürümlerde) kaydederek.</span><span class="sxs-lookup"><span data-stu-id="bdba2-133">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> extension method in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="bdba2-134">Temel olarak, barındırılan Hizmetleri, `ConfigureServices()` `Startup` tipik bir ASP.net Webhost öğesinden aşağıdaki kodda olduğu gibi, sınıfının tanıdık bir yöntemi içine kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdba2-134">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddHostedService<GracePeriodManagerService>();
    services.AddHostedService<MyHostedServiceB>();
    services.AddHostedService<MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="bdba2-135">Bu kodda, `GracePeriodManagerService` barındırılan hizmet eShopOnContainers 'Daki sıralama iş mikro hizmetinden gerçek koddur, diğer ikisi de yalnızca iki ek örnek olur.</span><span class="sxs-lookup"><span data-stu-id="bdba2-135">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="bdba2-136">`IHostedService`Arka plan görevi yürütme, uygulamanın yaşam süresi (Bu konuyla ilgili konak veya mikro hizmet) ile birlikte düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="bdba2-136">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="bdba2-137">Uygulama başlatıldığında görevleri kaydeder ve uygulama kapatılırken düzgün bir şekilde işlem yapmak veya temizlemek için bir fırsattır.</span><span class="sxs-lookup"><span data-stu-id="bdba2-137">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="bdba2-138">Kullanmadan `IHostedService` , herhangi bir görevi çalıştırmak için her zaman bir arka plan iş parçacığı başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdba2-138">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="bdba2-139">Bu iş parçacığı, sorunsuz temizleme eylemleri çalıştırma fırsatına gerek kalmadan yalnızca uygulamanın kapanma zamanına göre farklılık gösteren bir fark vardır.</span><span class="sxs-lookup"><span data-stu-id="bdba2-139">The difference is precisely at the app's shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="bdba2-140">Ihostedservice arabirimi</span><span class="sxs-lookup"><span data-stu-id="bdba2-140">The IHostedService interface</span></span>

<span data-ttu-id="bdba2-141">Bir kaydettiğinizde `IHostedService` , .NET Core `StartAsync()` `StopAsync()` `IHostedService` uygulama başlatma ve durdurma sırasında, sizin yazmanız için ve yöntemlerini çağıracaktır.</span><span class="sxs-lookup"><span data-stu-id="bdba2-141">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="bdba2-142">Daha fazla ayrıntı için [ıhostedservice arabirimine](https://docs.microsoft.com/aspnet/core/fundamentals/host/hosted-services?view=aspnetcore-3.1&tabs=visual-studio#ihostedservice-interface) başvurun</span><span class="sxs-lookup"><span data-stu-id="bdba2-142">For more details, refer [IHostedService interface](https://docs.microsoft.com/aspnet/core/fundamentals/host/hosted-services?view=aspnetcore-3.1&tabs=visual-studio#ihostedservice-interface)</span></span>

<span data-ttu-id="bdba2-143">Imagine kullanabileceğiniz gibi, birden çok ıhostedservice uygulaması oluşturabilir ve bu Hizmetleri `ConfigureService()` daha önce gösterildiği gibi, yöntemde de dı kapsayıcısına kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdba2-143">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="bdba2-144">Bu barındırılan tüm hizmetler uygulama/mikro hizmetle birlikte başlatılır ve durdurulur.</span><span class="sxs-lookup"><span data-stu-id="bdba2-144">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="bdba2-145">Bir geliştirici olarak, bir `StopAsync()` Yöntem ana bilgisayar tarafından tetiklendiğinde hizmetlerinizin durdurma eylemini işlemekten siz sorumlusunuz.</span><span class="sxs-lookup"><span data-stu-id="bdba2-145">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="bdba2-146">Arka plan hizmeti temel sınıfından türeten özel bir barındırılan hizmet sınıfıyla ıhostedservice 'i uygulama</span><span class="sxs-lookup"><span data-stu-id="bdba2-146">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="bdba2-147">Devam edip özel barındırılan hizmet sınıfınızı sıfırdan oluşturabilir ve `IHostedService` .NET Core 2,0 kullanırken yapmanız gereken şekilde uygulamasını uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdba2-147">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="bdba2-148">Ancak, çoğu arka plan görevinin, iptal belirteçleri yönetimi ve diğer tipik işlemlerle ilgili benzer ihtiyaçlarına sahip olacağı için, `BackgroundService` (.NET Core 2,1 sürümünden itibaren kullanılabilir) adlı öğesinden türetilebilir uygun bir soyut temel sınıf vardır.</span><span class="sxs-lookup"><span data-stu-id="bdba2-148">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="bdba2-149">Bu sınıf, arka plan görevini kurmak için gereken ana işi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdba2-149">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="bdba2-150">Sonraki kod, .NET Core 'da uygulanan şekilde soyut BackgroundService taban sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="bdba2-150">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

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

<span data-ttu-id="bdba2-151">Bu devralınan uygulama için bir önceki soyut temel sınıftan türetirken, `ExecuteAsync()` bir veritabanını yoklayarak ve gerektiğinde tümleştirme olaylarını yayımlayan eShopOnContainers 'dan olduğu gibi, özel bir barındırılan hizmet sınıfınıza yöntemi uygulamanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="bdba2-151">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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
        // Constructor's parameters validations...
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
            // and publishing events into the Event Bus (RabbitMQ / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

<span data-ttu-id="bdba2-152">EShopOnContainers için bu özel durumda, belirli bir duruma sahip siparişleri bulmak için bir veritabanı tablosunu sorgulayan bir uygulama yöntemi yürütüyor ve değişiklikler uygulanırken, tümleştirme olayları olay veri yolu aracılığıyla yayımlanıyor (bunun altında, Kbbitmq veya Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="bdba2-152">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="bdba2-153">Kuşkusuz, bunun yerine başka bir iş arka plan görevini çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdba2-153">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="bdba2-154">Varsayılan olarak, iptal belirteci 5 saniyelik bir zaman aşımıyla ayarlanır, ancak bu değeri `WebHost` , uzantısını kullanarak oluştururken de değiştirebilirsiniz `UseShutdownTimeout` `IWebHostBuilder` .</span><span class="sxs-lookup"><span data-stu-id="bdba2-154">By default, the cancellation token is set with a 5 seconds timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="bdba2-155">Bu, hizmetimizin 5 saniye içinde iptal etmek beklenen, aksi takdirde daha aniden sonlandırabilecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bdba2-155">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="bdba2-156">Aşağıdaki kod bu süreyi 10 saniyeye değiştiriyor.</span><span class="sxs-lookup"><span data-stu-id="bdba2-156">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="bdba2-157">Özet sınıf diyagramı</span><span class="sxs-lookup"><span data-stu-id="bdba2-157">Summary class diagram</span></span>

<span data-ttu-id="bdba2-158">Aşağıdaki görüntüde, ıhostedservices 'i uygularken dahil olan sınıfların ve arabirimlerin görsel bir özeti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bdba2-158">The following image shows a visual summary of the classes and interfaces involved when implementing IHostedServices.</span></span>

![Iwebhost ve IHOST 'un birçok hizmeti barındırabir şekilde gösteren diyagram.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

<span data-ttu-id="bdba2-160">**Şekil 6-27**.</span><span class="sxs-lookup"><span data-stu-id="bdba2-160">**Figure 6-27**.</span></span> <span data-ttu-id="bdba2-161">Ihostedservice ile ilgili birden çok sınıfı ve arabirimi gösteren sınıf diyagramı</span><span class="sxs-lookup"><span data-stu-id="bdba2-161">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

<span data-ttu-id="bdba2-162">Sınıf diyagramı: ıwebhost ve IHOST, ıhostedservice 'i uygulayan BackgroundService 'ten kalıtımla alınan birçok hizmeti barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="bdba2-162">Class diagram: IWebHost and IHost can host many services, which inherit from BackgroundService, which implements IHostedService.</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="bdba2-163">Dağıtım değerlendirmeleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="bdba2-163">Deployment considerations and takeaways</span></span>

<span data-ttu-id="bdba2-164">ASP.NET Core veya .NET Core ' u dağıtırken, `WebHost` son çözümü etkileyebilecek şekilde dikkat etmeniz önemlidir `Host` .</span><span class="sxs-lookup"><span data-stu-id="bdba2-164">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="bdba2-165">Örneğin, uygulamanızı `WebHost` IIS 'de veya düzenli bir Azure App Service dağıtırsanız, uygulama havuzu geri dönüştürme nedeniyle ana bilgisayarınız kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="bdba2-165">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="bdba2-166">Ancak, ana bilgisayarınızı bir kapsayıcı olarak Kubernetes gibi bir Orchestrator 'a dağıtıyorsanız, ana bilgisayarınızda bulunan canlı örnek sayısını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdba2-166">But if you are deploying your host as a container into an orchestrator like Kubernetes, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="bdba2-167">Ayrıca, Azure Işlevleri gibi bu senaryolar için bulutta yapılan diğer yaklaşımları de göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdba2-167">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="bdba2-168">Son olarak, hizmetin tüm zamanı çalıştırması ve bir Windows Server üzerinde dağıtımı gerekiyorsa, bir Windows hizmeti kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdba2-168">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="bdba2-169">Ancak `WebHost` , bir uygulama havuzuna dağıtılan bir uygulama için bile, hala geçerli olacak şekilde uygulamanın bellek içi önbelleğini yeniden doldurma veya temizleme gibi senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="bdba2-169">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application's in-memory cache that would be still applicable.</span></span>

<span data-ttu-id="bdba2-170">`IHostedService`Arabirim, bir ASP.NET Core Web uygulamasında (.net core 2,0 ve sonraki sürümlerde) veya herhangi bir işlem/konakta (.net core 2,1 ile başlayarak) arka plan görevleri başlatmak için kullanışlı bir yol sağlar `IHost` .</span><span class="sxs-lookup"><span data-stu-id="bdba2-170">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0 and later versions) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="bdba2-171">Ana avantajı, ana bilgisayarın kendisi kapatılırken arka plan görevlerinizin kodunu temizlemek için sorunsuz iptalle elde ettiğiniz fırsatdır.</span><span class="sxs-lookup"><span data-stu-id="bdba2-171">Its main benefit is the opportunity you get with the graceful cancellation to clean-up the code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="bdba2-172">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="bdba2-172">Additional resources</span></span>

- <span data-ttu-id="bdba2-173">**ASP.NET Core/Standart 2,0 ' de zamanlanmış bir görev oluşturma** </span><span class="sxs-lookup"><span data-stu-id="bdba2-173">**Building a scheduled task in ASP.NET Core/Standard 2.0** </span></span>\
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="bdba2-174">**ASP.NET Core 2,0 ' de ıhostedservice 'i uygulama** </span><span class="sxs-lookup"><span data-stu-id="bdba2-174">**Implementing IHostedService in ASP.NET Core 2.0** </span></span>\
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="bdba2-175">**ASP.NET Core 2,1 kullanarak GenericHost örneği** </span><span class="sxs-lookup"><span data-stu-id="bdba2-175">**GenericHost Sample using ASP.NET Core 2.1** </span></span>\
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> <span data-ttu-id="bdba2-176">[Önceki](test-aspnet-core-services-web-apps.md) 
>  [Sonraki](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="bdba2-176">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
