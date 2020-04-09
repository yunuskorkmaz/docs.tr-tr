---
title: IHostedService ve BackgroundService sınıfı ile mikro hizmetlerde arka plan görevlerini uygulayın
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Microservices .NET Core'da arka plan görevlerini uygulamak için IHostedService ve BackgroundService'i kullanmak için yeni seçenekleri anlayın.
ms.date: 01/30/2020
ms.openlocfilehash: fd26d0444312d3525ad95b2273f28a6ceaa27911
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988342"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="8ccf0-103">IHostedService ve BackgroundService sınıfı ile mikro hizmetlerde arka plan görevlerini uygulayın</span><span class="sxs-lookup"><span data-stu-id="8ccf0-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="8ccf0-104">Arka plan görevleri ve zamanlanmış işler, sonunda, bir mikrohizmet tabanlı uygulamada veya herhangi bir uygulamada uygulama yapmanız gereken bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="8ccf0-105">Bir microservices mimarisi kullanırken fark, bu arka plan görevlerini barındırmak için tek bir microservice işlemi/kapsayıcı uygulayabilmenizdir, böylece gerektiğinde küçültebilirsiniz/yukarı ya da hatta bu mikrohizmet işleminin/kapsayıcının tek bir örneğini çalıştırdığından emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="8ccf0-106">Genel bir bakış açısından, .NET Core'da bu tür görevler *barındırılan hizmetler*olarak adlandırdık, çünkü bunlar ana bilgisayar/uygulama/microservice içinde barındırdığınız hizmetler/mantık.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="8ccf0-107">Bu durumda, barındırılan hizmetin yalnızca arka plan görev mantığına sahip bir sınıf anlamına geldiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="8ccf0-108">.NET Core 2.0'dan bu yana, <xref:Microsoft.Extensions.Hosting.IHostedService> framework barındırılan hizmetleri kolayca uygulamanıza yardımcı olan yeni bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="8ccf0-109">Temel fikir, 6-26 görüntüde gösterildiği gibi, web ana bilgisayarınız veya ana bilgisayarınız çalışırken arka planda çalışan birden çok arka plan görevlerini (barındırılan hizmetleri) kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-109">The basic idea is that you can register multiple background tasks (hosted services) that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![Diyagram Core IWebHost ve .NET Core IHost ASP.NET karşılaştırarak.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

<span data-ttu-id="8ccf0-111">**Şekil 6-26**.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-111">**Figure 6-26**.</span></span> <span data-ttu-id="8ccf0-112">IHostedService'i Bir WebHost'ta kullanma ve Bir Ana Bilgisayar</span><span class="sxs-lookup"><span data-stu-id="8ccf0-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="8ccf0-113">ASP.NET Core 1.x ve `IWebHost` 2.x web uygulamalarında arka plan işlemleri için destek.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-113">ASP.NET Core 1.x and 2.x support `IWebHost` for background processes in web apps.</span></span> <span data-ttu-id="8ccf0-114">.NET Core 2.1 ve `IHost` sonraki sürümler düz konsol uygulamaları ile arka plan işlemleri için destek.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-114">.NET Core 2.1 and later versions support `IHost` for background processes with plain console apps.</span></span> <span data-ttu-id="8ccf0-115">ve `Host`. arasında `WebHost` yapılan farka dikkat edin</span><span class="sxs-lookup"><span data-stu-id="8ccf0-115">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="8ccf0-116">Core `WebHost` 2.0ASP.NETbir (taban sınıf uygulama) `IWebHost`bir MVC web uygulaması veya Web API hizmeti uygularken gibi işlemiçin HTTP sunucu özellikleri sağlamak için kullandığınız altyapı artifakı olduğunu.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-116">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as when you're implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="8ccf0-117">bağımlılık enjeksiyonu, istek ardışık hatlarına ara yazılım ekleme ve benzeri ekleme yapmanızı sağlayan ASP.NET Core'daki tüm yeni altyapı iyiliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-117">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, and similar.</span></span> <span data-ttu-id="8ccf0-118">Arka `WebHost` plan görevleri `IHostedServices` için bu çok aynı kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-118">The `WebHost` uses these very same `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="8ccf0-119">.NET Core 2.1'de (taban `Host` sınıf uygulama) `IHost`tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-119">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="8ccf0-120">Temel olarak, bir `Host` (bağımlılık enjeksiyon, barındırılan hizmetler, vb) ile `WebHost` ne benzer bir altyapıya sahip sağlar, ama bu durumda, sadece mvc, Web API veya HTTP sunucu özellikleri ile ilgili hiçbir şey ile, ana bilgisayar olarak basit ve daha hafif bir süreç istiyorum.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-120">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="8ccf0-121">Bu nedenle, barındırılan hizmetleri işlemek `IHost` için özel bir ana bilgisayar işlemi oluşturabilir ve başka bir `IHostedServices`şey, böyle bir mikrohizmet sadece `WebHost`barındırma için yapılmış , ya da alternatif olarak mevcut bir ASP.NET Core uzatabilirsiniz , mevcut bir ASP.NET Core Web API veya MVC uygulaması gibi.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-121">Therefore, you can choose and either create a specialized host-process with `IHost` to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="8ccf0-122">Her yaklaşımın, iş ve ölçeklenebilirlik ihtiyaçlarınıza bağlı olarak artıları ve eksileri vardır.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-122">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="8ccf0-123">Alt satırda temelde arka plan görevleri HTTP (`IWebHost`) ile `IHost`ilgisi varsa kullanmanız gerektiğini .</span><span class="sxs-lookup"><span data-stu-id="8ccf0-123">The bottom line is basically that if your background tasks have nothing to do with HTTP (`IWebHost`) you should use `IHost`.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="8ccf0-124">Barındırılan hizmetleri WebHost veya Host'unuzda kaydetme</span><span class="sxs-lookup"><span data-stu-id="8ccf0-124">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="8ccf0-125">Kullanımı bir veya bir `IHostedService` `WebHost` `Host`'de oldukça benzer olduğundan arayüzü daha fazla detaya gidelim .</span><span class="sxs-lookup"><span data-stu-id="8ccf0-125">Let's drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="8ccf0-126">SignalR barındırılan hizmetleri kullanan bir yapı örneğidir, ancak aynı zamanda gibi çok basit şeyler için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8ccf0-126">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="8ccf0-127">Değişiklikleri arayan bir veritabanını yoklayan bir arka plan görevi.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-127">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="8ccf0-128">Bazı önbelleği düzenli aralıklarla güncelleştiren zamanlanmış bir görev.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-128">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="8ccf0-129">Bir görevin arka plan iş parçacığı üzerinde yürütülmesini sağlayan QueueBackgroundWorkItem uygulaması.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-129">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="8ccf0-130">Bir web uygulamasının arka planındaki ileti kuyruğundan gelen iletileri işleme alırken, bu tür `ILogger`ortak hizmetleri paylaşın.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-130">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="8ccf0-131">Bir arka plan `Task.Run()`görevi ile başladı.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-131">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="8ccf0-132">Temelde bu eylemlerden herhangi birini uygulayan bir arka `IHostedService`plan görevine boşaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-132">You can basically offload any of those actions to a background task that implements `IHostedService`.</span></span>

<span data-ttu-id="8ccf0-133">Bir veya birden fazla `IHostedServices` eklemenin `WebHost` veya `Host` <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>  uzantı yöntemiyle ASP.NET Core'a `WebHost` (veya `Host` .NET Core 2.1 ve üzeri bir girişte) kaydettirmeniz dir.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-133">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> extension method in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="8ccf0-134">Temel olarak, tipik bir ASP.NET WebHost aşağıdaki `Startup` kod olarak, sınıfın tanıdık `ConfigureServices()` yöntemi içinde barındırılan hizmetleri kaydetmek zorunda.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-134">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

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

<span data-ttu-id="8ccf0-135">Bu kodda, `GracePeriodManagerService` barındırılan hizmet eShopOnContainers sipariş iş microservice gerçek kodu, diğer iki ek örnek ise.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-135">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="8ccf0-136">Arka `IHostedService` plan görev yürütme uygulamanın ömrü (ana bilgisayar veya microservice, bu konuda) ile koordine edilir.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-136">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="8ccf0-137">Uygulama başladığında görevleri kaydedersiniz ve uygulama kapatılırken bazı zarif eylem veya temizleme yapma fırsatınız olur.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-137">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="8ccf0-138">`IHostedService`Kullanmadan, her zaman herhangi bir görevi çalıştırmak için bir arka plan iş parçacığı başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-138">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="8ccf0-139">Aradaki fark, uygulamanın kapatma süresinin tam olarak bu iş parçacığının zarif temizleme eylemleri çalıştırma fırsatına sahip olmadan öldürüleceği zamandır.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-139">The difference is precisely at the app's shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="8ccf0-140">IHostedService arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ccf0-140">The IHostedService interface</span></span>

<span data-ttu-id="8ccf0-141">Bir `IHostedService`, .NET Core kaydettiğinizde, `StopAsync()` uygulama `IHostedService` başlangıç `StartAsync()` ve durdurma sırasında türün ve yöntemin izini ve yöntemini sırasıyla çağırır.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-141">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="8ccf0-142">Özellikle, başlat sunucu başladıktan ve `IApplicationLifetime.ApplicationStarted` tetiklendikten sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-142">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="8ccf0-143">.NET Core'da tanımlandığı `IHostedService` gibi aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-143">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

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

<span data-ttu-id="8ccf0-144">Tahmin edebileceğiniz gibi, IHostedService'in birden çok uygulaması oluşturabilir `ConfigureService()` ve bunları daha önce gösterildiği gibi, yöntemde DI kapsayıcısına kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-144">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="8ccf0-145">Tüm bu barındırılan hizmetler başlatılacaktır ve uygulama / microservice ile birlikte durdurulur.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-145">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="8ccf0-146">Bir geliştirici olarak, `StopAsync()` yöntem ana bilgisayar tarafından tetiklendiğinde hizmetlerinizin durdurma eylemini işlemekten siz sorumlusunuz.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-146">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="8ccf0-147">BackgroundService taban sınıfından kaynaklanan özel barındırılan hizmet sınıfıyla IHostedService'i uygulama</span><span class="sxs-lookup"><span data-stu-id="8ccf0-147">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="8ccf0-148">.NET Core 2.0'ı kullanırken yapmanız `IHostedService`gereken özel barındırılan hizmet sınıfınızı sıfırdan oluşturabilir ve uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-148">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="8ccf0-149">Ancak, çoğu arka plan görevi, iptal belirteçleri yönetimi ve diğer tipik işlemlerle ilgili benzer ihtiyaçlara sahip `BackgroundService` olduğundan, (.NET Core 2.1'den beri kullanılabilir) adından da tanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-149">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="8ccf0-150">Bu sınıf, arka plan görevini ayarlamak için gereken temel çalışmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-150">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="8ccf0-151">Sonraki kod ,NET Core'da uygulanan soyut BackgroundService taban sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-151">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

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

<span data-ttu-id="8ccf0-152">Bir önceki soyut taban sınıftan türeyen, bu devralınan uygulama sayesinde, bir veritabanı yoklama ve gerektiğinde Olay Veri Servisi içine entegrasyon olayları yayımlama eShopOnContainers aşağıdaki basitleştirilmiş kod gibi, kendi özel barındırılan hizmet sınıfında `ExecuteAsync()` yöntemi uygulamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-152">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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

<span data-ttu-id="8ccf0-153">eShopOnContainers için bu özel durumda, belirli bir devlet ile siparişleri arayan bir veritabanı tablosu sorgulayan bir uygulama yöntemi yürütülür ve değişiklikleri uygularken, olay veri yolunda (altında RabbitMQ veya Azure Hizmet Veri Servisi kullanıyor olabilir) üzerinden entegrasyon olayları yayımlıyor.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-153">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="8ccf0-154">Tabii ki, bunun yerine, başka bir iş arka plan görev çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-154">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="8ccf0-155">Varsayılan olarak, iptal belirteci 5 saniyelik bir zaman kaybıyla ayarlanır, `WebHost` ancak `UseShutdownTimeout` 'nın `IWebHostBuilder`uzantısını kullanırken bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-155">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="8ccf0-156">Bu, hizmetimizin 5 saniye içinde iptal edilmesinin beklendiği, aksi takdirde daha ani bir şekilde öldürüleceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-156">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="8ccf0-157">Aşağıdaki kod bu süreyi 10 saniyeolarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-157">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="8ccf0-158">Özet sınıf diyagramı</span><span class="sxs-lookup"><span data-stu-id="8ccf0-158">Summary class diagram</span></span>

<span data-ttu-id="8ccf0-159">Aşağıdaki resimde, IHostedServices uygularken ilgili sınıfların ve arabirimlerin görsel bir özeti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-159">The following image shows a visual summary of the classes and interfaces involved when implementing IHostedServices.</span></span>

![IWebHost ve IHost birçok hizmet barındırabilir gösteren diyagram.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

<span data-ttu-id="8ccf0-161">**Şekil 6-27**.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-161">**Figure 6-27**.</span></span> <span data-ttu-id="8ccf0-162">IHostedService ile ilgili birden çok sınıf ve arabirimi gösteren sınıf diyagramı</span><span class="sxs-lookup"><span data-stu-id="8ccf0-162">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

<span data-ttu-id="8ccf0-163">Sınıf diyagramı: IWebHost ve IHost, IHostedService uygulayan BackgroundService'ten devralınan birçok hizmeti barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-163">Class diagram: IWebHost and IHost can host many services, which inherit from BackgroundService, which implements IHostedService.</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="8ccf0-164">Dağıtım hususları ve paket ler</span><span class="sxs-lookup"><span data-stu-id="8ccf0-164">Deployment considerations and takeaways</span></span>

<span data-ttu-id="8ccf0-165">ASP.NET Core `WebHost` veya .NET Core'unuzu `Host` dağıtma şeklinizin nihai çözümü etkileyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-165">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="8ccf0-166">Örneğin, `WebHost` IIS'de veya normal bir Azure Uygulama Hizmetine dağıtırsanız, ana bilgisayarınız uygulama havuzu geri dönüşümleri nedeniyle kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-166">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="8ccf0-167">Ancak ev sahibinizi Kubernetes gibi bir orkestratöre konteyner olarak dağıtıyorsanız, ev sahibinizin emin sayıda canlı örneğini kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-167">But if you are deploying your host as a container into an orchestrator like Kubernetes, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="8ccf0-168">Ayrıca, bulutta özellikle Bu Senaryolar için yapılan Azure İşlevler gibi diğer yaklaşımları da göz önünde bulundurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-168">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="8ccf0-169">Son olarak, hizmetin sürekli çalışıyor olması gerekiyorsa ve bir Windows Server'da dağıtılıyorsanız, bir Windows Hizmeti kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-169">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="8ccf0-170">Ancak, bir `WebHost` uygulama havuzuna dağıtılan bir uygulama için bile, uygulamanın bellek içi önbelleğini yeniden doldurma veya yıkama gibi hala geçerli olacak senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-170">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application's in-memory cache that would be still applicable.</span></span>

<span data-ttu-id="8ccf0-171">Arabirim, `IHostedService` arka plan görevlerini ASP.NET Core web uygulamasında (.NET Core 2.0 ve sonraki sürümlerde) veya herhangi bir işlem/ana bilgisayarda (.NET Core 2.1 ile başlayarak) başlatmak için `IHost`kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-171">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0 and later versions) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="8ccf0-172">Ana bilgisayarın en büyük avantajı, ana bilgisayar kapatılırken arka plan görevlerinizin temizleme kodunu temizlemek için zarif iptal ile elde ettiğiniz fırsattır.</span><span class="sxs-lookup"><span data-stu-id="8ccf0-172">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8ccf0-173">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="8ccf0-173">Additional resources</span></span>

- <span data-ttu-id="8ccf0-174">**ASP.NET Core/Standard 2.0'da zamanlanmış bir görev oluşturma** </span><span class="sxs-lookup"><span data-stu-id="8ccf0-174">**Building a scheduled task in ASP.NET Core/Standard 2.0** </span></span>\
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="8ccf0-175">**Core 2.0'da IHostedService'in uygulanması ASP.NET** </span><span class="sxs-lookup"><span data-stu-id="8ccf0-175">**Implementing IHostedService in ASP.NET Core 2.0** </span></span>\
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="8ccf0-176">**ASP.NET Core 2.1 kullanarak GenericHost Örnek** </span><span class="sxs-lookup"><span data-stu-id="8ccf0-176">**GenericHost Sample using ASP.NET Core 2.1** </span></span>\
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> <span data-ttu-id="8ccf0-177">[Önceki](test-aspnet-core-services-web-apps.md)
> [Sonraki](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="8ccf0-177">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
