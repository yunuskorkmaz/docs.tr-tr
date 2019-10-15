---
title: Ihostedservice ve BackgroundService sınıfıyla mikro hizmetlerde arka plan görevleri uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Mikro hizmetler .NET Core 'da arka plan görevleri uygulamak için ıhostedservice ve BackgroundService kullanmak üzere yeni seçenekleri anlayın.
ms.date: 01/07/2019
ms.openlocfilehash: ad91268925ad36d5b60d5d0601eee7544b79ab2e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318678"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="35fef-103">Ihostedservice ve BackgroundService sınıfıyla mikro hizmetlerde arka plan görevleri uygulama</span><span class="sxs-lookup"><span data-stu-id="35fef-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="35fef-104">Arka plan görevleri ve zamanlanan işler, sonunda, mikro hizmet tabanlı bir uygulamada veya herhangi bir uygulama türünde uygulamanız gerekebilecek bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="35fef-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="35fef-105">Mikro hizmet mimarisi kullanmanın farkı, bu arka plan görevlerini barındırmak için tek bir mikro hizmet işlemi/kapsayıcı uygulayabilmenizi sağlayacak ve bu sayede, ihtiyacınız olduğu kadar ölçeklendirebilmeniz için veya tek bir örneğini çalıştırmasını sağlayabilirsiniz. Mikro hizmet işlemi/kapsayıcısı.</span><span class="sxs-lookup"><span data-stu-id="35fef-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="35fef-106">.NET Core 'da, genel bir bakış noktasından, ana bilgisayar/uygulama/mikro hizmetiniz içinde barındırmanıza yönelik hizmetler/mantık olduklarından, bu tür görevler *barındırılan hizmetler*olarak adlandırdık.</span><span class="sxs-lookup"><span data-stu-id="35fef-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="35fef-107">Bu durumda, barındırılan hizmetin arka plan görevi mantığına sahip bir sınıf anlamına geldiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="35fef-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="35fef-108">.NET Core 2,0 sürümünden itibaren Framework, barındırılan Hizmetleri kolayca uygulamanıza yardımcı olan <xref:Microsoft.Extensions.Hosting.IHostedService> adlı yeni bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="35fef-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="35fef-109">Temel düşünce, 6-26 görüntüsünde gösterildiği gibi, Web ana bilgisayarınız veya ana bilgisayarınız çalışırken arka planda çalışan birden fazla arka plan görevini (barındırılan hizmetler) kaydedebilmeniz için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35fef-109">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![ASP.NET Core 1. x ve 2. x desteği Web Apps 'te arka plan işlemlerinde, .NET Core 2, 1, düz konsol uygulamalarıyla arka plan işlemlerinde IHOST 'u destekler.](./media/image26.png)

<span data-ttu-id="35fef-111">**Şekil 6-26**.</span><span class="sxs-lookup"><span data-stu-id="35fef-111">**Figure 6-26**.</span></span> <span data-ttu-id="35fef-112">Bir WebHost 'de ıhostedservice kullanma ve bir ana bilgisayar</span><span class="sxs-lookup"><span data-stu-id="35fef-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="35fef-113">@No__t-0 ve `Host` arasında yapılan farkı dikkate alın.</span><span class="sxs-lookup"><span data-stu-id="35fef-113">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="35fef-114">ASP.NET Core 2,0 ' de bir `WebHost` (`IWebHost` uygulayan temel sınıf), işleme bir MVC web uygulaması veya Web API hizmeti uygulama gibi HTTP sunucu özellikleri sağlamak için kullandığınız altyapı yapıtıdır.</span><span class="sxs-lookup"><span data-stu-id="35fef-114">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="35fef-115">ASP.NET Core, bağımlılık ekleme, istek ardışık düzeninde middlewares ekleme, vb. gibi tüm yeni altyapıyı her şekilde sağlar ve arka plan görevleri için bu @no__t tam olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="35fef-115">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="35fef-116">.NET Core 2,1 ' de bir `Host` (`IHost` uygulayan temel sınıf) eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="35fef-116">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="35fef-117">Temel olarak, bir `Host`, `WebHost` (bağımlılık ekleme, barındırılan hizmetler vb.) ile sahip olduğunuz kadar benzer bir altyapıya sahip etmenize olanak tanır, ancak bu durumda yalnızca konak olarak, MVC, Web API 'SI veya HTTP sunucusu özellikleri.</span><span class="sxs-lookup"><span data-stu-id="35fef-117">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="35fef-118">Bu nedenle, barındırılan Hizmetleri işlemek için IHOST ile özelleştirilmiş bir konak oluşturma ve başka hiçbir şey yapma (örneğin, yalnızca `IHostedServices` ' ı barındırmak için yapılan bir mikro hizmet) veya var olan bir ASP.NET Core `WebHost` ' i de genişletebilirsiniz mevcut ASP.NET Core Web API 'SI veya MVC uygulaması.</span><span class="sxs-lookup"><span data-stu-id="35fef-118">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="35fef-119">Her yaklaşımın iş ve ölçeklenebilirlik gereksinimlerinize bağlı olarak profesyonelleri ve dezavantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="35fef-119">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="35fef-120">Arka plan görevleriniz, HTTP (ıwebhost) ile hiçbir şey yapmayabilir ve IHOST kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="35fef-120">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use IHost.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="35fef-121">Barındırılan Hizmetleri WebHost veya ana bilgisayarınıza kaydetme</span><span class="sxs-lookup"><span data-stu-id="35fef-121">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="35fef-122">@No__t-0 arabiriminde daha fazla ayrıntıya giderek, kullanımı bir `WebHost` veya `Host` içinde oldukça benzer.</span><span class="sxs-lookup"><span data-stu-id="35fef-122">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="35fef-123">SignalR, barındırılan Hizmetleri kullanan bir yapıtın örneğidir, ancak şu gibi daha basit şeyler için de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="35fef-123">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="35fef-124">Arka plan görevi, değişiklik isteyen bir veritabanını yoklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="35fef-124">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="35fef-125">Belirli bir önbelleği düzenli aralıklarla güncelleştiren zamanlanmış bir görev.</span><span class="sxs-lookup"><span data-stu-id="35fef-125">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="35fef-126">Bir görevin arka plan iş parçacığında yürütülmesini sağlayan QueueBackgroundWorkItem 'ın bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="35fef-126">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="35fef-127">@No__t-0 gibi ortak hizmetleri paylaşırken bir Web uygulamasının arka planında bir ileti kuyruğundan ileti işleme.</span><span class="sxs-lookup"><span data-stu-id="35fef-127">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="35fef-128">@No__t-0 ile başlayan bir arka plan görevi.</span><span class="sxs-lookup"><span data-stu-id="35fef-128">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="35fef-129">Bu eylemlerin herhangi birini temel olarak ıhostedservice temelli bir arka plan görevine devreolursunuz.</span><span class="sxs-lookup"><span data-stu-id="35fef-129">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="35fef-130">@No__t-1 veya `Host` ' ye bir veya daha fazla @no__t (veya .NET Core 2,1 ve üzeri) bir ASP.NET Core `WebHost` ' e (ya da bir `Host` ' e) kayıt yaptırın.</span><span class="sxs-lookup"><span data-stu-id="35fef-130">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="35fef-131">Temel olarak, barındırılan Hizmetleri, tipik bir ASP.NET WebHost 'ten aşağıdaki kodda olduğu gibi, `Startup` sınıfının tanıdık `ConfigureServices()` yöntemi içine kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="35fef-131">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

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

<span data-ttu-id="35fef-132">Bu kodda, `GracePeriodManagerService` barındırılan hizmeti eShopOnContainers 'daki sıralama iş mikro hizmetinden gerçek koddur; diğer ikisi de yalnızca iki ek örnek olur.</span><span class="sxs-lookup"><span data-stu-id="35fef-132">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="35fef-133">@No__t-0 arka plan görevi yürütme, uygulamanın yaşam süresi (ana bilgisayar veya mikro hizmet) ile birlikte düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="35fef-133">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="35fef-134">Uygulama başlatıldığında görevleri kaydeder ve uygulama kapatılırken düzgün bir şekilde işlem yapmak veya temizlemek için bir fırsattır.</span><span class="sxs-lookup"><span data-stu-id="35fef-134">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="35fef-135">@No__t-0 kullanmadan, herhangi bir görevi çalıştırmak için her zaman bir arka plan iş parçacığı başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35fef-135">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="35fef-136">Bu iş parçacığı, sorunsuz temizleme eylemleri çalıştırma fırsatına gerek kalmadan yalnızca uygulamanın kapanma zamanına göre farklılık gösteren bir fark vardır.</span><span class="sxs-lookup"><span data-stu-id="35fef-136">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="35fef-137">Ihostedservice arabirimi</span><span class="sxs-lookup"><span data-stu-id="35fef-137">The IHostedService interface</span></span>

<span data-ttu-id="35fef-138">Bir @no__t kaydettiğinizde, .NET Core, uygulama başlatma ve durdurma sırasında `IHostedService` türünde `StartAsync()` ve `StopAsync()` yöntemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="35fef-138">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="35fef-139">Özellikle, sunucu başladıktan sonra başlatma çağrılır ve `IApplicationLifetime.ApplicationStarted` tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="35fef-139">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="35fef-140">.NET Core 'da tanımlanan `IHostedService`, aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="35fef-140">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

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

<span data-ttu-id="35fef-141">Imagine kullanabileceğiniz gibi, birden çok ıhostedservice uygulaması oluşturabilir ve bu hizmetleri daha önce gösterildiği gibi, `ConfigureService()` yönteminde dı kapsayıcısına kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35fef-141">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="35fef-142">Bu barındırılan tüm hizmetler uygulama/mikro hizmetle birlikte başlatılır ve durdurulur.</span><span class="sxs-lookup"><span data-stu-id="35fef-142">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="35fef-143">Bir geliştirici olarak, ana bilgisayar tarafından `StopAsync()` yöntemi tetiklendiğinde hizmetlerinizin durdurma eylemini işlemekten siz sorumlusunuz.</span><span class="sxs-lookup"><span data-stu-id="35fef-143">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="35fef-144">Arka plan hizmeti temel sınıfından türeten özel bir barındırılan hizmet sınıfıyla ıhostedservice 'i uygulama</span><span class="sxs-lookup"><span data-stu-id="35fef-144">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="35fef-145">Daha sonra, .NET Core 2,0 kullanırken yapmanız gereken şekilde, sıfırdan özel barındırılan hizmet sınıfınızı oluşturabilir ve `IHostedService` ' ı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35fef-145">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="35fef-146">Ancak, çoğu arka plan görevinin, iptal belirteçleri yönetimi ve diğer tipik işlemlerle ilgili benzer ihtiyaçlarına sahip olacağı için, `BackgroundService` (.NET Core 2,1 sürümünden itibaren kullanılabilir) adlı, öğesinden türetilebilir uygun bir soyut temel sınıf vardır.</span><span class="sxs-lookup"><span data-stu-id="35fef-146">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="35fef-147">Bu sınıf, arka plan görevini kurmak için gereken ana işi sağlar.</span><span class="sxs-lookup"><span data-stu-id="35fef-147">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="35fef-148">Sonraki kod, .NET Core 'da uygulanan şekilde soyut BackgroundService taban sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="35fef-148">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

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

<span data-ttu-id="35fef-149">Bu devralınan uygulama sayesinde, önceki soyut temel sınıftan türettikten sonra yalnızca kendi özel barındırılan hizmet sınıfınıza `ExecuteAsync()` yöntemini uygulamanız gerekir. Bu, bir tarafından yoklama yapan eShopOnContainers 'dan aşağıdaki Basitleştirilmiş kodda bulunur. gerektiğinde olay veri yolundaki tümleştirme olaylarını veritabanı ve yayımlama.</span><span class="sxs-lookup"><span data-stu-id="35fef-149">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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
            // and publishing events into the Event Bus (RabbitMQ / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

<span data-ttu-id="35fef-150">EShopOnContainers için bu özel durumda, belirli bir duruma sahip siparişleri bulmak için bir veritabanı tablosunu sorgulayan bir uygulama yöntemi yürütüyor ve değişiklikler uygulanırken, tümleştirme olayları olay veri yolu aracılığıyla yayımlanıyor (Bu durum Oybbitmq veya Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="35fef-150">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="35fef-151">Kuşkusuz, bunun yerine başka bir iş arka plan görevini çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35fef-151">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="35fef-152">Varsayılan olarak, iptal belirteci 5 saniyelik bir zaman aşımıyla ayarlanır, ancak `WebHost` ' ı oluştururken `IWebHostBuilder` ' nin `UseShutdownTimeout` uzantısını kullanarak bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35fef-152">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="35fef-153">Bu, hizmetimizin 5 saniye içinde iptal etmek beklenen, aksi takdirde daha aniden sonlandırabilecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="35fef-153">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="35fef-154">Aşağıdaki kod bu süreyi 10 saniyeye değiştiriyor.</span><span class="sxs-lookup"><span data-stu-id="35fef-154">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="35fef-155">Özet sınıf diyagramı</span><span class="sxs-lookup"><span data-stu-id="35fef-155">Summary class diagram</span></span>

<span data-ttu-id="35fef-156">Aşağıdaki görüntüde, ıhostedservices 'i uygularken dahil olan sınıfların ve arabirimlerin görsel bir özeti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="35fef-156">The following image shows a visual summary of the classes and interfaces involved when implementing IHostedServices.</span></span>

![Sınıf diyagramı: ıwebhost ve IHOST, ıhostedservice 'i uygulayan BackgroundService 'ten kalıtımla alınan birçok hizmeti barındırabilir.](./media/image27.png)

<span data-ttu-id="35fef-158">**Şekil 6-27**.</span><span class="sxs-lookup"><span data-stu-id="35fef-158">**Figure 6-27**.</span></span> <span data-ttu-id="35fef-159">Ihostedservice ile ilgili birden çok sınıfı ve arabirimi gösteren sınıf diyagramı</span><span class="sxs-lookup"><span data-stu-id="35fef-159">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="35fef-160">Dağıtım değerlendirmeleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="35fef-160">Deployment considerations and takeaways</span></span>

<span data-ttu-id="35fef-161">ASP.NET Core `WebHost` veya .NET Core `Host` ' i dağıttığınız şekilde, son çözümü etkilediğine dikkat etmeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="35fef-161">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="35fef-162">Örneğin, `WebHost` ' ı IIS veya normal Azure App Service dağıtırsanız, uygulama havuzu geri dönüştürme nedeniyle ana bilgisayarınız kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="35fef-162">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="35fef-163">Ancak, ana bilgisayarınızı bir kapsayıcı olarak Kubernetes veya Service Fabric gibi bir Orchestrator 'a dağıtıyorsanız, ana bilgisayarınızda bulunan canlı örnek sayısını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35fef-163">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="35fef-164">Ayrıca, Azure Işlevleri gibi bu senaryolar için bulutta yapılan diğer yaklaşımları de göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="35fef-164">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="35fef-165">Son olarak, hizmetin tüm zamanı çalıştırması ve bir Windows Server üzerinde dağıtımı gerekiyorsa, bir Windows hizmeti kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35fef-165">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="35fef-166">Ancak, bir uygulama havuzuna dağıtılan `WebHost` için bile, uygulamanın bellek içi önbelleğini yeniden doldurma veya temizleme gibi senaryolar vardır. Bu, hala geçerli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="35fef-166">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="35fef-167">@No__t-0 arabirimi, bir ASP.NET Core Web uygulamasında (.NET Core 2,0) veya herhangi bir işlem/konakta (.NET Core 2,1 ' de `IHost` ' den başlayarak) arka plan görevleri başlatmak için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="35fef-167">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="35fef-168">Ana avantajı, ana bilgisayarın kendisi kapatılırken arka plan görevlerinizin kodunu temizlemek için sorunsuz iptalle elde ettiğiniz fırsatdır.</span><span class="sxs-lookup"><span data-stu-id="35fef-168">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="35fef-169">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="35fef-169">Additional resources</span></span>

- <span data-ttu-id="35fef-170">**ASP.NET Core/Standart 2,0 ' de zamanlanmış bir görev oluşturma**</span><span class="sxs-lookup"><span data-stu-id="35fef-170">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span>  
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="35fef-171">**ASP.NET Core 2,0 ' de ıhostedservice 'i uygulama**</span><span class="sxs-lookup"><span data-stu-id="35fef-171">**Implementing IHostedService in ASP.NET Core 2.0**</span></span>  
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="35fef-172">**ASP.NET Core 2,1 kullanarak GenericHost örneği**</span><span class="sxs-lookup"><span data-stu-id="35fef-172">**GenericHost Sample using ASP.NET Core 2.1**</span></span>  
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
><span data-ttu-id="35fef-173">[Önceki](test-aspnet-core-services-web-apps.md)
>[İleri](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="35fef-173">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
