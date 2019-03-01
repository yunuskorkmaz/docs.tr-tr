---
title: Ihostedservice ve BackgroundService sınıfı ile mikro hizmetler içindeki arka plan görevlerini uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | .NET Core mikro hizmetler arka plan görevleri uygulamak için Ihostedservice ve BackgroundService kullanılacak yeni seçeneklerini anlayın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 638c9b9bae97b90b94c0ca9b421bc20cd3eb41ee
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967197"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="1ad2e-103">Ihostedservice ve BackgroundService sınıfı ile mikro hizmetler içindeki arka plan görevlerini uygulama</span><span class="sxs-lookup"><span data-stu-id="1ad2e-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="1ad2e-104">Arka plan görevleri ve zamanlanmış işleri, sonuç olarak, bir mikro hizmet tabanlı uygulama veya uygulama herhangi bir türden uygulamak için ihtiyacınız olabilecek bir şey var.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="1ad2e-105">Bir mikro hizmet mimarisi kullanırken, bir tek bir mikro hizmet işlemi/ihtiyacınız veya bile, tek bir örneği çalıştığından emin olmak, aşağı/yukarı ölçeklendirebilirsiniz bu arka plan görevlerinin barındırılması için kapsayıcı uygulayabileceğiniz fark mikro hizmet işlemi/kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="1ad2e-106">Bir genel bakış açısıyla, .NET Core Biz bu tür bir görev çağrılır *barındırılan Hizmetler*, çünkü bunlar, ana bilgisayar/uygulama/mikro hizmet içinde ana bilgisayar Hizmetleri/mantığı.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="1ad2e-107">Bu durumda, barındırılan hizmetin yalnızca bir sınıf ile arka plan görevi mantıksal anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="1ad2e-108">.NET Core 2.0 beri framework adlı yeni bir arabirim sağlar. <xref:Microsoft.Extensions.Hosting.IHostedService> kolayca barındırılan uygulama hizmetleri için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="1ad2e-109">Temel web ana arka planda çalışan birden fazla arka plan görevleri (barındırılan hizmetler) kaydedebilirsiniz veya konağın çalıştığından, 6-26 görüntüde gösterildiği gibi olur.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-109">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![Web uygulamaları, .NET Core, ASP.NET Core 1.x ve 2.x'i desteği IWebHost arka plan 2,1 destekler IHost düz konsol uygulamaları ile arka plan işlemleri için işler.](./media/image26.png)

<span data-ttu-id="1ad2e-111">**Şekil 6-26**.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-111">**Figure 6-26**.</span></span> <span data-ttu-id="1ad2e-112">Bir ana bilgisayar ve bir Web barındırma Ihostedservice kullanma</span><span class="sxs-lookup"><span data-stu-id="1ad2e-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="1ad2e-113">Yapılan arasındaki farka dikkat edin `WebHost` ve `Host`.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-113">Note the difference made between `WebHost` and `Host`.</span></span> 

<span data-ttu-id="1ad2e-114">A `WebHost` (temel sınıf uygulama `IWebHost`) HTTP sunucusu özellikleri IF gibi işleme sağlamak için kullandığınız altyapı yapıt uygulayan bir MVC web uygulaması veya Web API'si hizmeti ASP.NET Core 2.0 sürümünde olduğu.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-114">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="1ad2e-115">ASP.NET Core, bağımlılık ekleme, istek ardışık düzeni, vb. middlewares eklemek ve tam olarak bu kullanmak sağlayarak yeni tüm altyapı özelliği sağlar `IHostedServices` arka plan görevleri için.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-115">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="1ad2e-116">A `Host` (temel sınıf uygulama `IHost`) .NET Core 2.1 içinde kullanılmaya başlandı.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-116">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="1ad2e-117">Temel olarak, bir `Host` ile sahip daha benzer bir altyapıya sahip sağlar `WebHost` (bağımlılık ekleme, barındırılan hizmetler, vb.), ancak bu durumda, yalnızca basit ve daha hafif bir işlem, MVC için ilgili hiçbir şey barındırmasını istiyorsanız , Web API'si veya HTTP sunucusu özellikleri.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-117">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="1ad2e-118">Bu nedenle, seçebileceğiniz ve barındırılan hizmetler ve başka bir şey işlemek için yalnızca barındırmak için yapılan mikro IHost ile özel bir ana bilgisayar işlemi oluşturun `IHostedServices`, veya alternatif olarak, mevcut bir ASP.NET Core genişletebilirsiniz `WebHost` , mevcut bir ASP.NET Core Web API'si veya MVC uygulaması gibi.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-118">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span> 

<span data-ttu-id="1ad2e-119">Artıları ve eksileri iş ve ölçeklenebilirlik ihtiyaçlarınıza bağlı olarak her bir yaklaşıma sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-119">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="1ad2e-120">Alt çizgi, temelde arka plan görevlerinizi HTTP (IWebHost IHost kullanmanız gerekir) ile hiçbir ilişkisi varsa ortaya olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-120">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use IHost.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="1ad2e-121">WebHost veya konak Hizmetleri'nde barındırılan kaydediliyor</span><span class="sxs-lookup"><span data-stu-id="1ad2e-121">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="1ad2e-122">Şimdi ayrıntıya azaltma hakkında daha fazla `IHostedService` kullanımını oldukça benzer olduğundan arabirim bir `WebHost` veya bir `Host`.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-122">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span> 

<span data-ttu-id="1ad2e-123">SignalR, barındırılan hizmetler kullanarak bir yapıt örneği olmakla birlikte, gibi çok daha kolay şeyler için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1ad2e-123">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

-   <span data-ttu-id="1ad2e-124">Değişiklikleri isteyen bir veritabanı yoklama bir arka plan görevi.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-124">A background task polling a database looking for changes.</span></span>
-   <span data-ttu-id="1ad2e-125">Bazı önbellek düzenli olarak güncelleştirme, zamanlanmış bir görev.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-125">A scheduled task updating some cache periodically.</span></span>
-   <span data-ttu-id="1ad2e-126">Arka plan iş parçacığında çalıştırılacak bir görev sağlar QueueBackgroundWorkItem uygulaması.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-126">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
-   <span data-ttu-id="1ad2e-127">Ortak Hizmetleri paylaşırken arka planda bir web uygulamasının bir ileti kuyruktan ileti işleme `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-127">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
-   <span data-ttu-id="1ad2e-128">Bir arka plan görevi kullanmaya `Task.Run()`.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-128">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="1ad2e-129">Ihostedservice tabanlı bir arka plan görevi için bu eylemlerden herhangi birini temel boşaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-129">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="1ad2e-130">Bir veya daha çok eklediğiniz şekilde `IHostedServices` içine, `WebHost` veya `Host` bunları oluşturan bir ASP.NET Core, standard DI (bağımlılık ekleme) aracılığıyla kaydederek olan `WebHost` (veya bir `Host` .NET Core 2.1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="1ad2e-130">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="1ad2e-131">Barındırılan hizmetler bilinen içinde kaydetmek zorunda temelde, `ConfigureServices()` yöntemi `Startup` aşağıdaki kod tipik bir ASP.NET Web barındırma olduğu gibi bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-131">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span> 

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

<span data-ttu-id="1ad2e-132">Bu kodda, `GracePeriodManagerService` barındırılan hizmet gerçek koddan sıralama iş mikro hizmetine, diğer iki yalnızca iki ek örnekleri.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-132">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="1ad2e-133">`IHostedService` Arka plan görev yürütme uygulaması (konak veya mikro hizmet sorgunuzun) ömrünü koordine.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-133">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="1ad2e-134">Uygulama başladığında ve bazı normal eylemi gerçekleştirin veya uygulama kapatılıyor, temizleme fırsatına sahip görevleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-134">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="1ad2e-135">Kullanmadan `IHostedService`, herhangi bir görev çalıştırmak için bir arka plan iş parçacığı her zaman başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-135">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="1ad2e-136">Tam olarak uygulamanın kapatma zaman zaman iş parçacığı yalnızca fırsatı Normal temizleme eylemleri çalıştırmak zorunda kalmadan sonlandırılan farktır.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-136">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="1ad2e-137">Ihostedservice arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ad2e-137">The IHostedService interface</span></span>

<span data-ttu-id="1ad2e-138">Kaydettiğinizde bir `IHostedService`, .NET Core çağıracaktır `StartAsync()` ve `StopAsync()` yöntemleri, `IHostedService` uygulama başlatma sırasında yazın ve durdurur.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-138">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="1ad2e-139">Özellikle, sunucu yeniden başlatıldıktan sonra start çağrılır ve `IApplicationLifetime.ApplicationStarted` tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-139">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="1ad2e-140">`IHostedService` ' De .NET Core tanımlandığı gibi aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-140">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

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
<span data-ttu-id="1ad2e-141">Hayal edebileceğiniz gibi birden çok Ihostedservice uygulamaları oluşturabilir ve onları kaydetmek `ConfigureService()` yöntemi daha önce gösterildiği gibi DI kapsayıcıya alın.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-141">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="1ad2e-142">Bu barındırılan hizmetleri kullanmaya ve yanı sıra uygulama/mikro hizmet durduruldu.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-142">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="1ad2e-143">Bir geliştirici olarak durdurma eylemi veya hizmetlerinizi işlenmesinden sorumludur olduğunda `StopAsync()` yöntemi, ana bilgisayar tarafından tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-143">As a developer, you are responsible for handling the stopping action or your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="1ad2e-144">Ihostedservice ile BackgroundService temel sınıfından türetilen özel barındırılan hizmet sınıf uygulama</span><span class="sxs-lookup"><span data-stu-id="1ad2e-144">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="1ad2e-145">Durmayın sıfırdan özel bir barındırılan hizmet sınıfınızı oluşturma ve uygulama `IHostedService`gibi .NET Core 2.0 kullanarak yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-145">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span> 

<span data-ttu-id="1ad2e-146">Ancak, çoğu arka plan görevleri iptal belirteçlerini yönetimi ve diğer normal işlemleri in regard to benzer gereksinimleri olduğundan, yoktur, türetilebilir kullanışlı soyut temel sınıf adlı `BackgroundService` (.NET Core 2.1 sürümünden itibaren kullanılabilir).</span><span class="sxs-lookup"><span data-stu-id="1ad2e-146">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="1ad2e-147">Bu sınıf, arka plan görev oluşturmak için gereken ana çalışma sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-147">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="1ad2e-148">' De .NET Core uygulanan aynıdır, sonraki kodu BackgroundService soyut taban sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-148">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

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

<span data-ttu-id="1ad2e-149">Önceki Özet temel sınıf, devralınmış bu uygulama sayesinde'den türetilirken uygulamak yeterlidir `ExecuteAsync()` yöntemi kendi özel barındırılan hizmet sınıfı, aşağıda gösterildiği gibi sorgulanır hizmetine koddan Basitleştirilmiş bir veritabanı ve tümleştirme olayları olay gerektiğinde yoluna yayımlama.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-149">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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

    .../...
}
```

<span data-ttu-id="1ad2e-150">Bu belirli durumda hizmetine için belirli bir durumu siparişleri isteyen bir veritabanı tablosu sorgulanırken bir uygulama yöntemi yürütme ve değişiklikleri uygulanırken, olay veri yolu (underneath olabilir aracılığıyla tümleştirme olayları yayımlama RabbitMQ veya Azure Service Bus kullanarak).</span><span class="sxs-lookup"><span data-stu-id="1ad2e-150">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="1ad2e-151">Elbette, bunun yerine herhangi diğer iş arka plan görevini çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-151">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="1ad2e-152">Oluştururken bu değeri değiştirebilirsiniz ancak varsayılan olarak 5 ikinci zaman aşımı ile iptal belirteci ayarladıktan, `WebHost` kullanarak `UseShutdownTimeout` uzantısı `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-152">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="1ad2e-153">Bu, hizmetimiz 5 daha aniden sonlandırılacak saniye içinde aksi takdirde iptal beklenir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-153">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="1ad2e-154">Aşağıdaki kodu bu süre 10 saniye olarak değiştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-154">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="1ad2e-155">Özet sınıf diyagramı</span><span class="sxs-lookup"><span data-stu-id="1ad2e-155">Summary class diagram</span></span>

<span data-ttu-id="1ad2e-156">Aşağıdaki resimde bir görsel Özet sınıflarının ve interfaced IHostedServices uygularken ilgili gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-156">The following image shows a visual summary of the classes and interfaced involved when implementing IHostedServices.</span></span>
 
![Sınıf diyagramı: Ihostedservice uygulayan BackgroundService devralır birçok hizmet IWebHost ve IHost barındırabilirsiniz.](./media/image27.png)

<span data-ttu-id="1ad2e-158">**Şekil 6-27**.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-158">**Figure 6-27**.</span></span> <span data-ttu-id="1ad2e-159">Birden çok gösteren sınıf diyagramı Ihostedservice için ilgili sınıflar ve arabirimler</span><span class="sxs-lookup"><span data-stu-id="1ad2e-159">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="1ad2e-160">Dağıtım hakkında önemli noktalar ve paketler</span><span class="sxs-lookup"><span data-stu-id="1ad2e-160">Deployment considerations and takeaways</span></span>

<span data-ttu-id="1ad2e-161">ASP.NET Core dağıtma şeklinizi dikkat etmeniz önemlidir `WebHost` veya .NET Core `Host` nihai çözüm etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-161">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="1ad2e-162">Örneğin, dağıtırsanız, `WebHost` IIS veya normal bir Azure App Service, ana uygulama havuzu geri dönüştürülmeden nedeniyle kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-162">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="1ad2e-163">Ancak bir orchestrator Kubernetes veya Service Fabric uygulamasına kapsayıcı olarak konağınız dağıtıyorsanız, dinamik ana bilgisayar örneklerini garantili sayısını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-163">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="1ad2e-164">Ayrıca, Azure işlevleri gibi bu senaryolar için özellikle yapılan bulutta diğer yaklaşımlar deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-164">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="1ad2e-165">Son olarak, hizmetinin her zaman çalışıyor gerekir ve bir Windows sunucusuna dağıttığınız bir Windows hizmetini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-165">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="1ad2e-166">Ancak için bile bir `WebHost` bir uygulama havuzuna dağıtılmış, yeniden veya hala geçerli olacak uygulamanın bellek içi önbellek, temizleme gibi senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-166">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="1ad2e-167">`IHostedService` Arabirimi, web uygulaması (.NET Core 2.0 içinde) arka plan görevleri de bir ASP.NET Core başlatmak için kolay bir yol sağlar veya herhangi bir işlem/ana (.NET Core 2.1 ile başlayan `IHost`).</span><span class="sxs-lookup"><span data-stu-id="1ad2e-167">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="1ad2e-168">Konak kapatılıyor, arka plan görevlerinizi temizleme kodu için normal iptal ile alma fırsatı kendi ana avantajdır.</span><span class="sxs-lookup"><span data-stu-id="1ad2e-168">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="1ad2e-169">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="1ad2e-169">Additional resources</span></span>

-   <span data-ttu-id="1ad2e-170">**ASP.NET Core/Standard 2.0 zamanlanmış bir görev oluşturma**</span><span class="sxs-lookup"><span data-stu-id="1ad2e-170">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span> <br/>
    [*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   <span data-ttu-id="1ad2e-171">**ASP.NET Core 2.0 Ihostedservice uygulama**</span><span class="sxs-lookup"><span data-stu-id="1ad2e-171">**Implementing IHostedService in ASP.NET Core 2.0**</span></span> <br/>
    [*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   <span data-ttu-id="1ad2e-172">**GenericHost ASP.NET Core 2.1 kullanma örneği**</span><span class="sxs-lookup"><span data-stu-id="1ad2e-172">**GenericHost Sample using ASP.NET Core 2.1**</span></span> <br/>
    [*https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample*](https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample)

>[!div class="step-by-step"]
><span data-ttu-id="1ad2e-173">[Önceki](test-aspnet-core-services-web-apps.md)
>[İleri](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="1ad2e-173">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
