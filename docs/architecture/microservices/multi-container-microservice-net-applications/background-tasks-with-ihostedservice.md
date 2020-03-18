---
title: IHostedService ve BackgroundService sınıfı ile mikro hizmetlerde arka plan görevlerini uygulayın
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Microservices .NET Core'da arka plan görevlerini uygulamak için IHostedService ve BackgroundService'i kullanmak için yeni seçenekleri anlayın.
ms.date: 01/30/2020
ms.openlocfilehash: fab67c816e90c69a4d593422b4974cb9b8819807
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502302"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>IHostedService ve BackgroundService sınıfı ile mikro hizmetlerde arka plan görevlerini uygulayın

Arka plan görevleri ve zamanlanmış işler, sonunda, bir mikrohizmet tabanlı uygulamada veya herhangi bir uygulamada uygulama yapmanız gereken bir şeydir. Bir microservices mimarisi kullanırken fark, bu arka plan görevlerini barındırmak için tek bir microservice işlemi/kapsayıcı uygulayabilmenizdir, böylece gerektiğinde küçültebilirsiniz/yukarı ya da hatta bu mikrohizmet işleminin/kapsayıcının tek bir örneğini çalıştırdığından emin olabilirsiniz.

Genel bir bakış açısından, .NET Core'da bu tür görevler *barındırılan hizmetler*olarak adlandırdık, çünkü bunlar ana bilgisayar/uygulama/microservice içinde barındırdığınız hizmetler/mantık. Bu durumda, barındırılan hizmetin yalnızca arka plan görev mantığına sahip bir sınıf anlamına geldiğini unutmayın.

.NET Core 2.0'dan bu yana, <xref:Microsoft.Extensions.Hosting.IHostedService> framework barındırılan hizmetleri kolayca uygulamanıza yardımcı olan yeni bir arabirim sağlar. Temel fikir, 6-26 görüntüde gösterildiği gibi, web ana bilgisayarınız veya ana bilgisayarınız çalışırken arka planda çalışan birden çok arka plan görevlerini (barındırılan hizmetleri) kaydedebilirsiniz.

![Diyagram Core IWebHost ve .NET Core IHost ASP.NET karşılaştırarak.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

**Şekil 6-26**. IHostedService'i Bir WebHost'ta kullanma ve Bir Ana Bilgisayar

ASP.NET Core 1.x ve `IWebHost` 2.x web uygulamalarında arka plan işlemleri için destek. .NET Core 2.1 ve `IHost` sonraki sürümler düz konsol uygulamaları ile arka plan işlemleri için destek. ve `Host`. arasında `WebHost` yapılan farka dikkat edin

Core `WebHost` 2.0ASP.NETbir (taban sınıf uygulama) `IWebHost`bir MVC web uygulaması veya Web API hizmeti uygularken gibi işlemiçin HTTP sunucu özellikleri sağlamak için kullandığınız altyapı artifakı olduğunu. bağımlılık enjeksiyonu, istek ardışık hatlarına ara yazılım ekleme ve benzeri ekleme yapmanızı sağlayan ASP.NET Core'daki tüm yeni altyapı iyiliğini sağlar. Arka `WebHost` plan görevleri `IHostedServices` için bu çok aynı kullanır.

.NET Core 2.1'de (taban `Host` sınıf uygulama) `IHost`tanıtıldı. Temel olarak, bir `Host` (bağımlılık enjeksiyon, barındırılan hizmetler, vb) ile `WebHost` ne benzer bir altyapıya sahip sağlar, ama bu durumda, sadece mvc, Web API veya HTTP sunucu özellikleri ile ilgili hiçbir şey ile, ana bilgisayar olarak basit ve daha hafif bir süreç istiyorum.

Bu nedenle, barındırılan hizmetleri işlemek `IHost` için özel bir ana bilgisayar işlemi oluşturabilir ve başka bir `IHostedServices`şey, böyle bir mikrohizmet sadece `WebHost`barındırma için yapılmış , ya da alternatif olarak mevcut bir ASP.NET Core uzatabilirsiniz , mevcut bir ASP.NET Core Web API veya MVC uygulaması gibi.

Her yaklaşımın, iş ve ölçeklenebilirlik ihtiyaçlarınıza bağlı olarak artıları ve eksileri vardır. Alt satırda temelde arka plan görevleri HTTP (`IWebHost`) ile `IHost`ilgisi varsa kullanmanız gerektiğini .

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Barındırılan hizmetleri WebHost veya Host'unuzda kaydetme

Kullanımı bir veya bir `IHostedService` `WebHost` `Host`'de oldukça benzer olduğundan arayüzü daha fazla detaya gidelim .

SignalR barındırılan hizmetleri kullanan bir yapı örneğidir, ancak aynı zamanda gibi çok basit şeyler için kullanabilirsiniz:

- Değişiklikleri arayan bir veritabanını yoklayan bir arka plan görevi.
- Bazı önbelleği düzenli aralıklarla güncelleştiren zamanlanmış bir görev.
- Bir görevin arka plan iş parçacığı üzerinde yürütülmesini sağlayan QueueBackgroundWorkItem uygulaması.
- Bir web uygulamasının arka planındaki ileti kuyruğundan gelen iletileri işleme alırken, bu tür `ILogger`ortak hizmetleri paylaşın.
- Bir arka plan `Task.Run()`görevi ile başladı.

Temelde bu eylemlerden herhangi birini uygulayan bir arka `IHostedService`plan görevine boşaltabilirsiniz.

Bir veya birden fazla `IHostedServices` eklemenin `WebHost` veya `Host` <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>  uzantı yöntemiyle ASP.NET Core'a `WebHost` (veya `Host` .NET Core 2.1 ve üzeri bir girişte) kaydettirmeniz dir. Temel olarak, tipik bir ASP.NET WebHost aşağıdaki `Startup` kod olarak, sınıfın tanıdık `ConfigureServices()` yöntemi içinde barındırılan hizmetleri kaydetmek zorunda.

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

Bu kodda, `GracePeriodManagerService` barındırılan hizmet eShopOnContainers sipariş iş microservice gerçek kodu, diğer iki ek örnek ise.

Arka `IHostedService` plan görev yürütme uygulamanın ömrü (ana bilgisayar veya microservice, bu konuda) ile koordine edilir. Uygulama başladığında görevleri kaydedersiniz ve uygulama kapatılırken bazı zarif eylem veya temizleme yapma fırsatınız olur.

`IHostedService`Kullanmadan, her zaman herhangi bir görevi çalıştırmak için bir arka plan iş parçacığı başlatabilirsiniz. Aradaki fark, uygulamanın kapatma süresinin tam olarak bu iş parçacığının zarif temizleme eylemleri çalıştırma fırsatına sahip olmadan öldürüleceği zamandır.

## <a name="the-ihostedservice-interface"></a>IHostedService arabirimi

Bir `IHostedService`, .NET Core kaydettiğinizde, `StopAsync()` uygulama `IHostedService` başlangıç `StartAsync()` ve durdurma sırasında türün ve yöntemin izini ve yöntemini sırasıyla çağırır. Özellikle, başlat sunucu başladıktan ve `IApplicationLifetime.ApplicationStarted` tetiklendikten sonra çağrılır.

.NET Core'da tanımlandığı `IHostedService` gibi aşağıdaki gibi görünür.

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

Tahmin edebileceğiniz gibi, IHostedService'in birden çok uygulaması oluşturabilir `ConfigureService()` ve bunları daha önce gösterildiği gibi, yöntemde DI kapsayıcısına kaydedebilirsiniz. Tüm bu barındırılan hizmetler başlatılacaktır ve uygulama / microservice ile birlikte durdurulur.

Bir geliştirici olarak, `StopAsync()` yöntem ana bilgisayar tarafından tetiklendiğinde hizmetlerinizin durdurma eylemini işlemekten siz sorumlusunuz.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>BackgroundService taban sınıfından kaynaklanan özel barındırılan hizmet sınıfıyla IHostedService'i uygulama

.NET Core 2.0'ı kullanırken yapmanız `IHostedService`gereken özel barındırılan hizmet sınıfınızı sıfırdan oluşturabilir ve uygulamanız gerekir.

Ancak, çoğu arka plan görevi, iptal belirteçleri yönetimi ve diğer tipik işlemlerle ilgili benzer ihtiyaçlara sahip `BackgroundService` olduğundan, (.NET Core 2.1'den beri kullanılabilir) adından da tanabilirsiniz.

Bu sınıf, arka plan görevini ayarlamak için gereken temel çalışmayı sağlar.

Sonraki kod ,NET Core'da uygulanan soyut BackgroundService taban sınıfıdır.

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

Bir önceki soyut taban sınıftan türeyen, bu devralınan uygulama sayesinde, bir veritabanı yoklama ve gerektiğinde Olay Veri Servisi içine entegrasyon olayları yayımlama eShopOnContainers aşağıdaki basitleştirilmiş kod gibi, kendi özel barındırılan hizmet sınıfında `ExecuteAsync()` yöntemi uygulamak gerekir.

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

eShopOnContainers için bu özel durumda, belirli bir devlet ile siparişleri arayan bir veritabanı tablosu sorgulayan bir uygulama yöntemi yürütülür ve değişiklikleri uygularken, olay veri yolunda entegrasyon olayları yayımlıyor (altında olabilir RabbitMQ veya Azure Servis Veri Servisi'ni kullanarak).

Tabii ki, bunun yerine, başka bir iş arka plan görev çalıştırabilirsiniz.

Varsayılan olarak, iptal belirteci 5 saniyelik bir zaman kaybıyla ayarlanır, `WebHost` ancak `UseShutdownTimeout` 'nın `IWebHostBuilder`uzantısını kullanırken bu değeri değiştirebilirsiniz. Bu, hizmetimizin 5 saniye içinde iptal edilmesinin beklendiği, aksi takdirde daha ani bir şekilde öldürüleceği anlamına gelir.

Aşağıdaki kod bu süreyi 10 saniyeolarak değiştirir.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Özet sınıf diyagramı

Aşağıdaki resimde, IHostedServices uygularken ilgili sınıfların ve arabirimlerin görsel bir özeti gösterilmektedir.

![IWebHost ve IHost birçok hizmet barındırabilir gösteren diyagram.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

**Şekil 6-27**. IHostedService ile ilgili birden çok sınıf ve arabirimi gösteren sınıf diyagramı

Sınıf diyagramı: IWebHost ve IHost, IHostedService uygulayan BackgroundService'ten devralınan birçok hizmeti barındırabilir.

### <a name="deployment-considerations-and-takeaways"></a>Dağıtım hususları ve paket ler

ASP.NET Core `WebHost` veya .NET Core'unuzu `Host` dağıtma şeklinizin nihai çözümü etkileyebileceğini unutmayın. Örneğin, `WebHost` IIS'de veya normal bir Azure Uygulama Hizmetine dağıtırsanız, ana bilgisayarınız uygulama havuzu geri dönüşümleri nedeniyle kapatılabilir. Ancak ev sahibinizi Kubernetes gibi bir orkestratöre konteyner olarak dağıtıyorsanız, ev sahibinizin emin sayıda canlı örneğini kontrol edebilirsiniz. Ayrıca, bulutta özellikle Bu Senaryolar için yapılan Azure İşlevler gibi diğer yaklaşımları da göz önünde bulundurabilirsiniz. Son olarak, hizmetin sürekli çalışıyor olması gerekiyorsa ve bir Windows Server'da dağıtılıyorsanız, bir Windows Hizmeti kullanabilirsiniz.

Ancak, bir `WebHost` uygulama havuzuna dağıtılan bir uygulama için bile, uygulamanın bellek içi önbelleğini yeniden doldurma veya yıkama gibi hala geçerli olacak senaryolar vardır.

Arabirim, `IHostedService` arka plan görevlerini ASP.NET Core web uygulamasında (.NET Core 2.0 ve sonraki sürümlerde) veya herhangi bir işlem/ana bilgisayarda (.NET Core 2.1 ile başlayarak) başlatmak için `IHost`kullanışlı bir yol sağlar. Ana bilgisayarın en büyük avantajı, ana bilgisayar kapatılırken arka plan görevlerinizin temizleme kodunu temizlemek için zarif iptal ile elde ettiğiniz fırsattır.

## <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET Core/Standard 2.0'da zamanlanmış bir görev oluşturma** \
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- **Core 2.0'da IHostedService'in uygulanması ASP.NET** \
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- **ASP.NET Core 2.1 kullanarak GenericHost Örnek** \
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
>[Önceki](test-aspnet-core-services-web-apps.md)
>[Sonraki](implement-api-gateways-with-ocelot.md)
