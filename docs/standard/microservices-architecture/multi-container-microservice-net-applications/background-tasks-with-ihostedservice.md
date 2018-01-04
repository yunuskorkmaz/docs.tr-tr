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
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Mikro IHostedService ve BackgroundService sınıfı ile arka plan görevlerini uygulama

Arka plan görevleri ve zamanlanmış işler, sonuç olarak, bir temel mikro hizmet uygulaması veya uygulama herhangi bir tür uygulamanız gerekebilir bir şey markalarıdır. Mikro mimarisi kullanırken, bir tek mikro hizmet işlemi/ihtiyacınız veya bile, tek bir örneğini çalışacağından emin olmak, aşağı/yukarı ölçeklendirebilirsiniz bu arka plan görevleri barındırma için kapsayıcı uygulayabileceğiniz farktır mikro hizmet işlemi/kapsayıcı.

Konak/uygulama/mikro hizmet içinde ana bilgisayar Hizmetleri/mantığı oldukları için bir genel bakış açısından, .NET Core biz görevleri barındırılan hizmetleri, bu tür çağrılır. Bu durumda, barındırılan hizmet yalnızca arka plan görevi mantığı ile bir sınıf anlamına gelir.

.NET Core 2.0 itibaren çerçevesini adlı yeni bir arabirim sağlar. <xref:Microsoft.Extensions.Hosting.IHostedService> kolayca barındırılan uygulama hizmetleri için yardımcı olur. Temel web barındırma arka planda çalışan birden fazla arka plan görevleri (barındırılan Hizmetleri) kaydedebilirsiniz veya konağın çalıştığından, aşağıdaki resimde gösterildiği gibi olur.

![](./media/image26.png)

**Şekil 8-25.** Bir konak karşılaştırması WebHost IHostedService kullanma

Arasında yapılan fark Not `WebHost` ve `Host`. A `WebHost` (sınıfı uygulama temel `IWebHost`) kullandığınız HTTP sunucusu özellikleri IF gibi işleme sağlamak için altyapı yapı bir MVC web uygulaması veya Web API hizmet uygulama ASP.NET Core 2. 0 ' olduğu. ASP.NET Core, bağımlılık ekleme, middlewares INSERT HTTP ardışık düzen, vb. ve bunlar tam olarak kullanmak sağlayarak yeni tüm altyapı güzelliklerine sağlar `IHostedServices` arka plan görevleri için.

A `Host` (sınıfı uygulama temel `IHost`), ancak, .NET Core 2.1 içinde yeni bir şeydir. Temel olarak, bir `Host` ile sahip daha benzer bir altyapı sahip olmanızı sağlar `WebHost` (bağımlılık ekleme, barındırılan hizmetleri, vb.), ancak bu durumda, yalnızca basit ve daha açık bir işlem, MVC için ilgili herhangi bir şeyin barındırmasını istiyorsanız , Web API veya HTTP sunucusu özellikleri.

Bu nedenle, seçebileceğiniz ve ya da barındırılan hizmetler ve başka bir şey işlemek için yalnızca barındırmak için yapılan mikro IHost ile özel bir ana bilgisayar işlemi oluşturmak `IHostedServices`, veya alternatevely mevcut bir ASP.NET Core genişletme `WebHost` , mevcut bir ASP.NET çekirdek Web API veya MVC uygulaması gibi. 

Her iki yaklaşımın Artıları ve eksileri iş ve ölçeklenebilirlik gereksinimlerinize bağlı olarak vardır. Arka plan görevleri hiçbir şey varsa, alt çizgi temelde olan HTTP kullanması gereken (IWebHost) ve IHost, kullanılabilir olduğunda .NET Core 2.1 ile yapmak için.

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>WebHost veya ana bilgisayar Hizmetleri'ni barındırılan kaydetme

Şimdi ayrıntıya aşağı hakkında daha fazla `IHostedService` kullanım oldukça benzer olduğundan arabirim bir `WebHost` veya bir `Host`. 

SignalR barındırılan hizmetleri kullanarak bir yapı örneğidir ancak siz de gibi daha kolay şeyler için kullanabilirsiniz:

-   Değişiklikleri arayan bir veritabanı yoklama bir arka plan görevi.
-   Bazı önbellek düzenli aralıklarla güncelleştirme, zamanlanmış bir görev.
-   Arka plan iş parçacığında yürütülecek bir görev verir QueueBackgroundWorkItem uygulaması.
-   Ortak Hizmetleri gibi paylaşırken bir web uygulaması arka planda bir iletiyi kuyruktan iletileri işleme `ILogger`.
-   Bir arka plan görevi kullanmaya `Task.Run()`.

Ayrıca, üzerinde IHostedService dayalı bir arka plan görevi için bu eylemlerden herhangi birini temelde boşaltabilir.

Bir veya daha çok eklediğiniz şekilde `IHostedServices` içine, `WebHost` veya `Host` onları oluşturan bir ASP.NET Core, standard DI (bağımlılık ekleme) aracılığıyla kaydederek olan `WebHost` (veya bir `Host` .NET Core 2.1 içinde). Temel olarak bilinen içinde barındırılan hizmetler kaydetmek zorunda `ConfigureServices()` yöntemi `Startup` olduğu gibi tipik bir ASP.NET WebHost alınan aşağıdaki kod sınıfı. 

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

Bu kod `GracePeriodManagerService` barındırılan hizmet eShopOnContainers içinde sıralama iş mikro gerçek kodundan, yalnızca iki ek örnekler diğer ikisidir.

`IHostedService` Arka plan görev yürütme (ana bilgisayar veya bu mikro) uygulama ömrü koordine. Uygulama başlar ve bazı normal bir işlem veya uygulama kapatma sırasında temizleme fırsatı görevleri kaydedin.

Kullanmadan `IHostedService`, her zaman herhangi bir görev çalıştırmak için bir arka plan iş parçacığı başlayabilirsiniz. Tam olarak, ne zaman bu iş parçacığı yalnızca Normal temizleme eylemlerini çalıştırmak için Fırsat gerek kalmadan sonlandırıldı uygulamanın kapatma zaman farktır.


## <a name="the-ihostedservice-interface"></a>IHostedService arabirimi

Kaydettiğinizde bir `IHostedService`, .NET Core çağıracaktır `StartAsync()` ve `StopAsync()` yöntemleri, `IHostedService` uygulama başlatma sırasında yazın ve sırasıyla durdurun. Sunucu başlatıldıktan sonra start özellikle denir ve `IApplicationLifetime.ApplicationStarted` tetiklenir.

`IHostedService` .NET Core tanımlandığı gibi aşağıdaki gibi görünüyor.

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
Hayal edebildiğiniz gibi IHostedService birden çok uygulamaları oluşturma ve onları kaydetme `ConfigureService()` daha önce gösterildiği gibi dı kapsayıcı yönteme. Bu barındırılan tüm hizmetleri kullanmaya ve yanı sıra uygulama/mikro hizmet durduruldu.

Bir geliştirici olarak durdurma eylemi veya hizmetlerinizi işlenmesinden sorumludur zaman `StopAsync()` yöntemi, ana bilgisayar tarafından tetiklenir.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>BackgroundService temel sınıfından türetilen özel barındırılan hizmet sınıfıyla IHostedService uygulama

Şimdi sıfırdan özel barındırılan hizmet sınıfı oluşturmak ve uygulamak `IHostedService`gibi .NET Core 2.0 kullanırken yapmanız gerekir. 

Bununla birlikte, çoğu arka plan görevleri iptal belirteçleri yönetimi ve diğer tipical işlemler in regard to benzer gereksinimleri gerekeceğinden, .NET Core 2.1, BackgroundService adlı türetilemeyeceğini çok kullanışlı bir Özet temel sınıf sağlama.

Bu sınıf, arka plan görevi ayarlamanız için gereken ana iş sağlar. Okuma ve yazma gerek kalmaması Bu sınıf .NET Core 2.1 Kitaplığı'nda gelecektir unutmayın.

Ancak, bu yazma süresi itibariyle .NET Core 2.1 yayınlanmamıştır. İle uyumlu olduğundan bu nedenle, .NET Core 2.0 kullanmakta olduğu eShopOnContainers biz yalnızca geçici olarak .NET Core 2.1 açık kaynak deposu (açık kaynak lisans dışındaki tüm özel lisans gerekmez) bu sınıftan ekleme .NET Core 2.0 geçerli IHostedService arabirimi. .NET Core 2.1 yayımlandığında, yalnızca doğru NuGet paketi noktası gerekir.

Sonraki Özet BackgroundService temel sınıf .NET Core 2.1 içinde uygulandığı şekilde kodudur.

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

Önceki Özet temel sınıf, bu devralınan uygulaması sayesinde'den türetilirken uygulamak yeterlidir `ExecuteAsync()` kendi özel yönteminde barındırılan hizmet sınıfı, aşağıdaki gibi sorgulanır eShopOnContainers koddan Basitleştirilmiş bir veritabanı ve tümleştirme olayları olay gerektiğinde yoluna yayımlama.

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

Bu belirli durumda eShopOnContainers için quering görmek bir veritabanı tablosu siparişleri belirli bir durumu ve değişiklikleri uygularken, olay veri yolu (underneath bu olabilir aracılığıyla tümleştirme olaylarını yayımlama olan uygulama yöntemini yürütüyor RabbitMQ veya Azure Service Bus kullanarak). 

Elbette, başka iş arka plan görevi, bunun yerine çalıştırabilir.

Oluştururken bu değeri değiştirebilirsiniz, ancak varsayılan olarak 5 ikinci zaman aşımı ile iptal belirteci ayarlanır, `WebHost` kullanarak `UseShutdownTimeout` uzantısı `IWebHostBuilder`. Başka bir deyişle, hizmetimizi 5 daha aniden sonlandırılacak saniye içinde aksi takdirde iptal beklenir.

Aşağıdaki kod bu süre için 10 saniye değiştirme.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Özet sınıf diyagramı

Aşağıdaki resimde 8-26 IHostedServices uygularken söz konusu interfaced ve görsel sınıflarını Özet gösterir.
 
![](./media/image27.png)

**Şekil 8-26.** Birden çok gösteren sınıf diyagramı IHostedService için ilgili sınıfları ve arabirimleri

### <a name="deployment-considerations-and-takeaways"></a>Dağıtım hakkında önemli noktalar ve paketler

ASP.NET Core dağıtma şeklinizi dikkate almak önemlidir `WebHost` veya .NET Core `Host` nihai çözüm etkileyebilir. Örneğin, dağıtırsanız, `WebHost` IIS veya normal bir Azure uygulama hizmeti, ana bilgisayarınız nedeniyle uygulama havuzu dönüştürür kapatılabilir. Ancak bir orchestrator Kubernetes veya Service Fabric gibi içine bir kapsayıcı olarak ana bilgisayarınız dağıtıyorsanız, ana bilgisayarınız Canlı örneklerini garantili sayısını kontrol edebilirsiniz. Ayrıca, diğer yaklaşımlar özellikle Azure işlevleri gibi bu senaryoları için yapılan bulutta düşünebilirsiniz. 

Ancak için bile bir `WebHost` bir uygulama havuzu dağıtıldı, yeniden veya hala geçerli olacak uygulamanın bellek içi önbellek temizleme gibi senaryo vardır.

`IHostedService` Arabirimi sağlayan bir ASP.NET Core arka plan görevlerini başlatmak için kolay bir yol web uygulamasında (.NET Core 2. 0'da) veya herhangi bir işlem/ana (.NET Core 2.1 ile başlangıç `IHost`). Kendi ana avantajı konak kapatma sırasında normal iptal edilmesini arka plan görevleri ile temizleme koduna alma fırsattır.


#### <a name="additional-resources"></a>Ek kaynaklar

-   **ASP.NET Core/standart 2.0 zamanlanmış bir görev oluşturma** 

    [*https://blog.maartenballiauw.be/POST/2017/08/01/Building-a-Scheduled-Cache-Updater-in-ASPNET-Core-2.HTML*](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   **ASP.NET Core 2.0 IHostedService uygulama** 

    [*https://www.stevejgordon.co.uk/ASP-NET-Core-2-ihostedservice*](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   **ASP.NET Core 2.1 barındırma örnekleri** 

    [*https://github.com/ASPNET/Hosting/Tree/dev/Samples/GenericHostSample*](https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample)



>[!div class="step-by-step"]
[Önceki] (test-aspnet-core-services-web-apps.md) [sonraki] (.. /microservice-ddd-cqrs-Patterns/index.MD)
