---
title: Ihostedservice ve BackgroundService sınıfıyla mikro hizmetlerde arka plan görevleri uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Mikro hizmetler .NET Core 'da arka plan görevleri uygulamak için ıhostedservice ve BackgroundService kullanmak üzere yeni seçenekleri anlayın.
ms.date: 01/07/2019
ms.openlocfilehash: ff263212536233bef85e9517442b4d7ed9eff115
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039881"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Ihostedservice ve BackgroundService sınıfıyla mikro hizmetlerde arka plan görevleri uygulama

Arka plan görevleri ve zamanlanan işler, sonunda, mikro hizmet tabanlı bir uygulamada veya herhangi bir uygulama türünde uygulamanız gerekebilecek bir şeydir. Mikro hizmet mimarisi kullanmanın farkı, bu arka plan görevlerini barındırmak için tek bir mikro hizmet işlemi/kapsayıcı uygulayabilmenizi sağlayacak ve bu sayede, ihtiyacınız olduğu kadar ölçeklendirebilmeniz için veya tek bir örneğini çalıştırmasını sağlayabilirsiniz. Mikro hizmet işlemi/kapsayıcısı.

.NET Core 'da, genel bir bakış noktasından, ana bilgisayar/uygulama/mikro hizmetiniz içinde barındırmanıza yönelik hizmetler/mantık olduklarından, bu tür görevler *barındırılan hizmetler*olarak adlandırdık. Bu durumda, barındırılan hizmetin arka plan görevi mantığına sahip bir sınıf anlamına geldiğini unutmayın.

.NET Core 2,0 sürümünden itibaren Framework, barındırılan Hizmetleri kolayca uygulamanıza yardımcı <xref:Microsoft.Extensions.Hosting.IHostedService> adlı yeni bir arabirim sağlar. Temel düşünce, 6-26 görüntüsünde gösterildiği gibi, Web ana bilgisayarınız veya ana bilgisayarınız çalışırken arka planda çalışan birden fazla arka plan görevini (barındırılan hizmetler) kaydedebilmeniz için de kullanılır.

![ASP.NET Core 1. x ve 2. x desteği Web Apps 'te arka plan işlemlerinde, .NET Core 2, 1, düz konsol uygulamalarıyla arka plan işlemlerinde IHOST 'u destekler.](./media/image26.png)

**Şekil 6-26**. Bir WebHost 'de ıhostedservice kullanma ve bir ana bilgisayar

`WebHost` Ve`Host`arasında yapılan farkı dikkate alın.

ASP.NET Core `WebHost` 2,0 ' de bir `IWebHost`(temel sınıf uygulayan), bir MVC web uygulaması veya Web API hizmeti uyguladığınızda, işlem uygulamanıza http sunucusu özellikleri sağlamak için kullandığınız altyapı yapıtıdır. ASP.NET Core, bağımlılık ekleme, istek ardışık düzeninde middlewares ekleme, vb. ve bunları `IHostedServices` arka plan görevleri için tam olarak kullanma imkanı sağlayan tüm yeni altyapıyı her şey sağlar.

.Net `Host` Core 2,1 ' de `IHost`bir (temel sınıf uygulayan) tanıtılmıştı. Temel olarak, `Host` sahip olduğunuz `WebHost` kadar benzer bir altyapıya sahip olmanız (bağımlılık ekleme, barındırılan hizmetler vb.), ancak bu durumda, MVC ile ilgili hiçbir şey olmadan ana bilgisayar olarak basit ve daha hafif bir işleme sahip olmak istersiniz , Web API 'SI veya HTTP sunucusu özellikleri.

Bu nedenle, barındırılan Hizmetleri işlemek için IHOST ile özelleştirilmiş bir konak işlemi oluşturabilir ve başka hiçbir şey yapmayabilir; Örneğin, yalnızca barındırmak `IHostedServices`için yapılan bir mikro hizmet veya mevcut bir ASP.NET Core genişletebilirsiniz `WebHost` Mevcut bir ASP.NET Core Web API 'SI veya MVC uygulaması gibi.

Her yaklaşımın iş ve ölçeklenebilirlik gereksinimlerinize bağlı olarak profesyonelleri ve dezavantajları vardır. Arka plan görevleriniz, HTTP (ıwebhost) ile hiçbir şey yapmayabilir ve IHOST kullanmanız gerekir.

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Barındırılan Hizmetleri WebHost veya ana bilgisayarınıza kaydetme

Kullanımı, içinde `IHostedService` `WebHost` veya `Host`' de oldukça benzer olduğundan arabirim üzerinde daha fazla ayrıntıya bakalım.

SignalR, barındırılan Hizmetleri kullanan bir yapıtın örneğidir, ancak şu gibi daha basit şeyler için de kullanabilirsiniz:

- Arka plan görevi, değişiklik isteyen bir veritabanını yoklamaktadır.
- Belirli bir önbelleği düzenli aralıklarla güncelleştiren zamanlanmış bir görev.
- Bir görevin arka plan iş parçacığında yürütülmesini sağlayan QueueBackgroundWorkItem 'ın bir uygulamasıdır.
- Gibi ortak Hizmetleri `ILogger`paylaşırken bir Web uygulamasının arka planında bir ileti kuyruğundan iletileri işleme.
- İle `Task.Run()`başlatılan bir arka plan görevi.

Bu eylemlerin herhangi birini temel olarak ıhostedservice temelli bir arka plan görevine devreolursunuz.

`WebHost` Veya `IHostedServices` `WebHost` `Host` ' a bir veya daha fazla ekleme yönteminiz, bunları bir ASP.NET Core (veya .NET Core 2,1 ve üzeri bir sürümünde) standart dı (bağımlılık ekleme) yoluyla kaydederek. `Host` Temel olarak, barındırılan Hizmetleri, tipik bir ASP.net Webhost öğesinden aşağıdaki `ConfigureServices()` kodda olduğu gibi `Startup` , sınıfının tanıdık bir yöntemi içine kaydetmeniz gerekir.

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

Bu kodda, `GracePeriodManagerService` barındırılan hizmet eshoponcontainers 'daki sıralama iş mikro hizmetinden gerçek koddur, diğer ikisi de yalnızca iki ek örnek olur.

`IHostedService` Arka plan görevi yürütme, uygulamanın yaşam süresi (Bu konuyla ilgili konak veya mikro hizmet) ile birlikte düzenlenir. Uygulama başlatıldığında görevleri kaydeder ve uygulama kapatılırken düzgün bir şekilde işlem yapmak veya temizlemek için bir fırsattır.

Kullanmadan `IHostedService`, herhangi bir görevi çalıştırmak için her zaman bir arka plan iş parçacığı başlatabilirsiniz. Bu iş parçacığı, sorunsuz temizleme eylemleri çalıştırma fırsatına gerek kalmadan yalnızca uygulamanın kapanma zamanına göre farklılık gösteren bir fark vardır.

## <a name="the-ihostedservice-interface"></a>Ihostedservice arabirimi

Bir `IHostedService`kaydettiğinizde, .NET Core uygulama başlatma ve durdurma sırasında `StartAsync()` , `StopAsync()` sizin `IHostedService` yazmanız için ve yöntemlerini çağıracaktır. Özellikle, sunucu başlatıldıktan ve `IApplicationLifetime.ApplicationStarted` tetiklendikten sonra başlangıç çağırılır.

.NET Core 'da tanımlanan şekildeaşağıdakigibigörünür.`IHostedService`

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

Imagine kullanabileceğiniz gibi, birden çok ıhostedservice uygulaması oluşturabilir ve bu hizmetleri daha önce gösterildiği gibi `ConfigureService()` , yöntemde de dı kapsayıcısına kaydedebilirsiniz. Bu barındırılan tüm hizmetler uygulama/mikro hizmetle birlikte başlatılır ve durdurulur.

Bir geliştirici olarak, bir `StopAsync()` Yöntem ana bilgisayar tarafından tetiklendiğinde hizmetlerinizin durdurma eylemini işlemekten siz sorumlusunuz.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Arka plan hizmeti temel sınıfından türeten özel bir barındırılan hizmet sınıfıyla ıhostedservice 'i uygulama

Devam edip özel barındırılan hizmet sınıfınızı sıfırdan oluşturabilir ve .NET Core 2,0 kullanırken yapmanız gereken şekilde `IHostedService`uygulamasını uygulayabilirsiniz.

Ancak, çoğu arka plan görevinin, iptal belirteçleri yönetimi ve diğer tipik işlemlerle ilgili benzer ihtiyaçlarına sahip olacağı için, (.NET Core 2,1 sürümünden itibaren kullanılabilir) adlı `BackgroundService` öğesinden türetilebilir uygun bir soyut temel sınıf vardır.

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

Bu devralınan uygulama sayesinde, önceki soyut temel sınıftan türetirken, `ExecuteAsync()` yöntemi, yokladığınız eshoponcontainers 'dan aşağıdaki Basitleştirilmiş kodda olduğu gibi kendi özel barındırılan hizmet sınıfınıza de uygulamanız gerekir bir veritabanı ve gerektiğinde tümleştirme olayları olay veri yolunda yayımlanıyor.

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

EShopOnContainers için bu özel durumda, belirli bir duruma sahip siparişleri bulmak için bir veritabanı tablosunu sorgulayan bir uygulama yöntemi yürütüyor ve değişiklikler uygulanırken, tümleştirme olayları olay veri yolu aracılığıyla yayımlanıyor (Bu durum Oybbitmq veya Azure Service Bus).

Kuşkusuz, bunun yerine başka bir iş arka plan görevini çalıştırabilirsiniz.

Varsayılan olarak, iptal belirteci 5 saniyelik bir zaman aşımıyla ayarlanır, ancak bunu `WebHost` `UseShutdownTimeout` kullanarak `IWebHostBuilder`bu değeri değiştirebilirsiniz. Bu, hizmetimizin 5 saniye içinde iptal etmek beklenen, aksi takdirde daha aniden sonlandırabilecek anlamına gelir.

Aşağıdaki kod bu süreyi 10 saniyeye değiştiriyor.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Özet sınıf diyagramı

Aşağıdaki görüntüde, ıhostedservices uygulama sırasında ilgili sınıfların ve arabirim sayısının görsel bir özeti gösterilmektedir.

![Sınıf diyagramı: Iwebhost ve IHOST, ıhostedservice 'i uygulayan BackgroundService 'ten kalıtımla alınan birçok hizmeti barındırabilir.](./media/image27.png)

**Şekil 6-27**. Ihostedservice ile ilgili birden çok sınıfı ve arabirimi gösteren sınıf diyagramı

### <a name="deployment-considerations-and-takeaways"></a>Dağıtım değerlendirmeleri ve özellikleri

ASP.NET Core `WebHost` veya .NET Core `Host` ' u dağıtırken, son çözümü etkileyebilecek şekilde dikkat etmeniz önemlidir. Örneğin, uygulamanızı `WebHost` IIS 'de veya düzenli bir Azure App Service dağıtırsanız, uygulama havuzu geri dönüştürme nedeniyle ana bilgisayarınız kapatılabilir. Ancak, ana bilgisayarınızı bir kapsayıcı olarak Kubernetes veya Service Fabric gibi bir Orchestrator 'a dağıtıyorsanız, ana bilgisayarınızda bulunan canlı örnek sayısını kontrol edebilirsiniz. Ayrıca, Azure Işlevleri gibi bu senaryolar için bulutta yapılan diğer yaklaşımları de göz önünde bulundurmanız gerekir. Son olarak, hizmetin tüm zamanı çalıştırması ve bir Windows Server üzerinde dağıtımı gerekiyorsa, bir Windows hizmeti kullanabilirsiniz.

Ancak, uygulama havuzuna `WebHost` dağıtılan bir uygulama için bile, uygulamanın bellek içi önbelleğini yeniden doldurma veya temizleme gibi senaryolar da uygulanabilir.

Arabirim `IHostedService` , bir ASP.NET Core Web uygulamasında (.NET Core 2,0) veya herhangi bir işlem/konakta (.NET Core 2,1 ile `IHost`başlayarak) arka plan görevleri başlatmak için kullanışlı bir yol sağlar. Ana avantajı, ana bilgisayarın kendisi kapatılırken arka plan görevlerinizin kodunu temizlemek için sorunsuz iptalle elde ettiğiniz fırsatdır.

## <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET Core/Standart 2,0 ' de zamanlanmış bir görev oluşturma**  
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- **ASP.NET Core 2,0 ' de ıhostedservice 'i uygulama**  
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- **ASP.NET Core 2,1 kullanarak GenericHost örneği**  
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
>[Önceki](test-aspnet-core-services-web-apps.md)İleri
>[](implement-api-gateways-with-ocelot.md)
