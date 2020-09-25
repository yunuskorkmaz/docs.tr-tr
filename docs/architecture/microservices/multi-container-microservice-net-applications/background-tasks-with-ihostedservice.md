---
title: Ihostedservice ve BackgroundService sınıfıyla mikro hizmetlerde arka plan görevleri uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Mikro hizmetler .NET Core 'da arka plan görevleri uygulamak için ıhostedservice ve BackgroundService kullanmak üzere yeni seçenekleri anlayın.
ms.date: 08/14/2020
ms.openlocfilehash: 279f9e0093deafab51e63d72dce233c8e9466a55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173360"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Ihostedservice ve BackgroundService sınıfıyla mikro hizmetlerde arka plan görevleri uygulama

Arka plan görevleri ve zamanlanan işler, mikro hizmetler mimari modelini takip etmeksizin, herhangi bir uygulamada kullanmanız gerekebilecek bir şeydir. Mikro hizmet mimarisi kullanmanın farkı, arka plan görevini, barındırmak üzere ayrı bir süreç/kapsayıcıda uygulayabileceğiniz için, ihtiyacınız olan temelinde ölçeklendirebilmeniz gerekir.

.NET Core 'da, genel bir bakış noktasından, ana bilgisayar/uygulama/mikro hizmetiniz içinde barındırmanıza yönelik hizmetler/mantık olduklarından, bu tür görevler *barındırılan hizmetler*olarak adlandırdık. Bu durumda, barındırılan hizmetin arka plan görevi mantığına sahip bir sınıf anlamına geldiğini unutmayın.

.NET Core 2,0 sürümünden itibaren Framework, <xref:Microsoft.Extensions.Hosting.IHostedService> barındırılan Hizmetleri kolayca uygulamanıza yardımcı adlı yeni bir arabirim sağlar. Temel düşünce, 6-26 görüntüsünde gösterildiği gibi Web ana bilgisayarınız veya ana bilgisayarınız çalışırken arka planda çalışan birden fazla arka plan görevini (barındırılan hizmetler) kaydedebilmeniz için kullanılır.

![ASP.NET Core ıwebhost ve .NET Core IHOST karşılaştırması.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

**Şekil 6-26**. Bir WebHost 'de ıhostedservice kullanma ve bir ana bilgisayar

`IWebHost`Web Apps 'te arka plan işlemlerine yönelik 1. x ve 2. x desteği ASP.NET Core. .NET Core 2,1 ve üzeri sürümleri, `IHost` düz konsol uygulamalarıyla arka plan süreçlerini destekler. Ve arasında yapılan farkı dikkate `WebHost` alın `Host` .

`WebHost`ASP.NET Core 2,0 ' de bir (temel sınıf uygulayan `IWebHost` ), bir MVC web uygulaması veya Web API hizmeti uygularken, Işlem uygulamanıza http sunucusu özellikleri sağlamak için kullandığınız altyapı yapıtıdır. ASP.NET Core, bağımlılık ekleme, istek ardışık düzeninde middlewares ekleme ve benzer şekilde tüm yeni altyapıyı bir araya getirir. , `WebHost` `IHostedServices` Arka plan görevleri için bu çok aynısını kullanır.

`Host` `IHost` .Net Core 2,1 ' de bir (temel sınıf uygulayan) tanıtılmıştı. Temel olarak, sahip `Host` olduğunuz kadar benzer bir altyapıya sahip olmanız `WebHost` (bağımlılık ekleme, barındırılan hizmetler vb.), ancak bu durumda, MVC, Web API 'SI veya http sunucu özellikleriyle ilgili hiçbir şey olmadan ana bilgisayar için basit ve daha hafif bir işleme sahip olmak istersiniz.

Bu nedenle, barındırılan Hizmetleri işlemek için ile özel bir konak oluşturma ve `IHost` başka hiçbir şey yapma (örneğin, yalnızca barındırmak için yapılan bir mikro hizmet) veya var olan bir `IHostedServices` `WebHost` ASP.NET Core Web API 'SI ya da MVC uygulaması gibi mevcut bir ASP.NET Core genişletebilirsiniz.

Her yaklaşımın iş ve ölçeklenebilirlik gereksinimlerinize bağlı olarak profesyonelleri ve dezavantajları vardır. Arka plan görevleriniz, kullanmanız gereken HTTP () ile hiçbir şey yapmayabilir `IWebHost` `IHost` .

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Barındırılan Hizmetleri WebHost veya ana bilgisayarınıza kaydetme

Kullanımı, içinde veya ' de oldukça benzer olduğundan arabirim üzerinde daha fazla ayrıntıya bakalım `IHostedService` `WebHost` `Host` .

SignalR, barındırılan Hizmetleri kullanan bir yapıtın örneğidir, ancak şu gibi daha basit şeyler için de kullanabilirsiniz:

- Arka plan görevi, değişiklik isteyen bir veritabanını yoklamaktadır.
- Belirli bir önbelleği düzenli aralıklarla güncelleştiren zamanlanmış bir görev.
- Bir görevin arka plan iş parçacığında yürütülmesini sağlayan QueueBackgroundWorkItem 'ın bir uygulamasıdır.
- Gibi ortak hizmetleri paylaşırken bir Web uygulamasının arka planında bir ileti kuyruğundan iletileri işleme `ILogger` .
- İle başlatılan bir arka plan görevi `Task.Run()` .

Bu eylemlerin herhangi birini, uygulayan bir arka plan görevine temelde devretmek `IHostedService` .

Veya ' a bir veya daha fazla ekleme yönteminiz, `IHostedServices` `WebHost` bunları bir `Host` <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>   ASP.NET Core genişletme yöntemiyle `WebHost` (veya `Host` .NET Core 2,1 ve üzeri sürümlerde) kaydederek. Temel olarak, barındırılan Hizmetleri, `ConfigureServices()` `Startup` tipik bir ASP.net Webhost öğesinden aşağıdaki kodda olduğu gibi, sınıfının tanıdık bir yöntemi içine kaydetmeniz gerekir.

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

Bu kodda, `GracePeriodManagerService` barındırılan hizmet eShopOnContainers 'Daki sıralama iş mikro hizmetinden gerçek koddur, diğer ikisi de yalnızca iki ek örnek olur.

`IHostedService`Arka plan görevi yürütme, uygulamanın yaşam süresi (Bu konuyla ilgili konak veya mikro hizmet) ile birlikte düzenlenir. Uygulama başlatıldığında görevleri kaydeder ve uygulama kapatılırken düzgün bir şekilde işlem yapmak veya temizlemek için bir fırsattır.

Kullanmadan `IHostedService` , herhangi bir görevi çalıştırmak için her zaman bir arka plan iş parçacığı başlatabilirsiniz. Bu iş parçacığı, sorunsuz temizleme eylemleri çalıştırma fırsatına gerek kalmadan yalnızca uygulamanın kapanma zamanına göre farklılık gösteren bir fark vardır.

## <a name="the-ihostedservice-interface"></a>Ihostedservice arabirimi

Bir kaydettiğinizde `IHostedService` , .NET Core `StartAsync()` `StopAsync()` `IHostedService` uygulama başlatma ve durdurma sırasında, sizin yazmanız için ve yöntemlerini çağıracaktır. Daha fazla ayrıntı için [ıhostedservice arabirimine](/aspnet/core/fundamentals/host/hosted-services?tabs=visual-studio&view=aspnetcore-3.1#ihostedservice-interface) başvurun

Imagine kullanabileceğiniz gibi, birden çok ıhostedservice uygulaması oluşturabilir ve bu Hizmetleri `ConfigureService()` daha önce gösterildiği gibi, yöntemde de dı kapsayıcısına kaydedebilirsiniz. Bu barındırılan tüm hizmetler uygulama/mikro hizmetle birlikte başlatılır ve durdurulur.

Bir geliştirici olarak, bir `StopAsync()` Yöntem ana bilgisayar tarafından tetiklendiğinde hizmetlerinizin durdurma eylemini işlemekten siz sorumlusunuz.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Arka plan hizmeti temel sınıfından türeten özel bir barındırılan hizmet sınıfıyla ıhostedservice 'i uygulama

Devam edip özel barındırılan hizmet sınıfınızı sıfırdan oluşturabilir ve `IHostedService` .NET Core 2,0 kullanırken yapmanız gereken şekilde uygulamasını uygulayabilirsiniz.

Ancak, çoğu arka plan görevinin, iptal belirteçleri yönetimi ve diğer tipik işlemlerle ilgili benzer ihtiyaçlarına sahip olacağı için, `BackgroundService` (.NET Core 2,1 sürümünden itibaren kullanılabilir) adlı öğesinden türetilebilir uygun bir soyut temel sınıf vardır.

Bu sınıf, arka plan görevini kurmak için gereken ana işi sağlar.

Sonraki kod, .NET Core 'da uygulanan şekilde soyut BackgroundService taban sınıfıdır.

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

Bu devralınan uygulama için bir önceki soyut temel sınıftan türetirken, `ExecuteAsync()` bir veritabanını yoklayarak ve gerektiğinde tümleştirme olaylarını yayımlayan eShopOnContainers 'dan olduğu gibi, özel bir barındırılan hizmet sınıfınıza yöntemi uygulamanız yeterlidir.

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

EShopOnContainers için bu özel durumda, belirli bir duruma sahip siparişleri bulmak için bir veritabanı tablosunu sorgulayan bir uygulama yöntemi yürütüyor ve değişiklikler uygulanırken, tümleştirme olayları olay veri yolu aracılığıyla yayımlanıyor (bunun altında, Kbbitmq veya Azure Service Bus).

Kuşkusuz, bunun yerine başka bir iş arka plan görevini çalıştırabilirsiniz.

Varsayılan olarak, iptal belirteci 5 saniyelik bir zaman aşımıyla ayarlanır, ancak bu değeri `WebHost` , uzantısını kullanarak oluştururken de değiştirebilirsiniz `UseShutdownTimeout` `IWebHostBuilder` . Bu, hizmetimizin 5 saniye içinde iptal etmek beklenen, aksi takdirde daha aniden sonlandırabilecek anlamına gelir.

Aşağıdaki kod bu süreyi 10 saniyeye değiştiriyor.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Özet sınıf diyagramı

Aşağıdaki görüntüde, ıhostedservices 'i uygularken dahil olan sınıfların ve arabirimlerin görsel bir özeti gösterilmektedir.

![Iwebhost ve IHOST 'un birçok hizmeti barındırabir şekilde gösteren diyagram.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

**Şekil 6-27**. Ihostedservice ile ilgili birden çok sınıfı ve arabirimi gösteren sınıf diyagramı

Sınıf diyagramı: ıwebhost ve IHOST, ıhostedservice 'i uygulayan BackgroundService 'ten kalıtımla alınan birçok hizmeti barındırabilir.

### <a name="deployment-considerations-and-takeaways"></a>Dağıtım değerlendirmeleri ve özellikleri

ASP.NET Core veya .NET Core ' u dağıtırken, `WebHost` son çözümü etkileyebilecek şekilde dikkat etmeniz önemlidir `Host` . Örneğin, uygulamanızı `WebHost` IIS 'de veya düzenli bir Azure App Service dağıtırsanız, uygulama havuzu geri dönüştürme nedeniyle ana bilgisayarınız kapatılabilir. Ancak, ana bilgisayarınızı bir kapsayıcı olarak Kubernetes gibi bir Orchestrator 'a dağıtıyorsanız, ana bilgisayarınızda bulunan canlı örnek sayısını kontrol edebilirsiniz. Ayrıca, Azure Işlevleri gibi bu senaryolar için bulutta yapılan diğer yaklaşımları de göz önünde bulundurmanız gerekir. Son olarak, hizmetin tüm zamanı çalıştırması ve bir Windows Server üzerinde dağıtımı gerekiyorsa, bir Windows hizmeti kullanabilirsiniz.

Ancak `WebHost` , bir uygulama havuzuna dağıtılan bir uygulama için bile, hala geçerli olacak şekilde uygulamanın bellek içi önbelleğini yeniden doldurma veya temizleme gibi senaryolar vardır.

`IHostedService`Arabirim, bir ASP.NET Core Web uygulamasında (.net core 2,0 ve sonraki sürümlerde) veya herhangi bir işlem/konakta (.net core 2,1 ile başlayarak) arka plan görevleri başlatmak için kullanışlı bir yol sağlar `IHost` . Ana avantajı, ana bilgisayarın kendisi kapatılırken arka plan görevlerinizin kodunu temizlemek için sorunsuz iptalle elde ettiğiniz fırsatdır.

## <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET Core/Standart 2,0 ' de zamanlanmış bir görev oluşturma** \
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- **ASP.NET Core 2,0 ' de ıhostedservice 'i uygulama** \
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- **ASP.NET Core 2,1 kullanarak GenericHost örneği** \
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> [Önceki](test-aspnet-core-services-web-apps.md) 
>  [Sonraki](implement-api-gateways-with-ocelot.md)
