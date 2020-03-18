---
title: Sistem durumunu izleme
description: Sağlık izleme uygulamanın bir yolunu keşfedin.
ms.date: 03/02/2020
ms.openlocfilehash: d3d2bc72cf29b3d1ac93191e7ff2bd827c9ee68d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401713"
---
# <a name="health-monitoring"></a>Sistem durumunu izleme

Sistem durumu izleme, konteynerlerinizin ve mikro hizmetlerinizin durumu hakkında neredeyse gerçek zamanlı bilgi sağlar. Sağlık izleme, mikro hizmetlerin işletiminin birçok yönü için önemlidir ve daha sonra açıklandığı gibi, orkestratörlerin aşamalı olarak kısmi uygulama yükseltmeleri gerçekleştirmeleri özellikle önemlidir.

Mikro hizmetler tabanlı uygulamalar, performans monitörlerini, zamanlayıcılarını ve orkestratörlerini çok sayıda hizmeti izlemek için genellikle sinyal veya sistem durumu denetimlerini kullanır. Hizmetler isteğe bağlı olarak veya bir zamanlamada bir tür "Yaşıyorum" sinyali gönderemiyorsa, güncelleştirmeleri dağıttığınızda uygulamanız risklerle karşı karşıya kalabilir veya hataları çok geç algılayabilir ve büyük kesintilere neden olabilecek basamaklı arızaları durduramayabilir.

Tipik modelde, hizmetler durumları hakkında raporlar gönderir ve bu bilgiler, uygulamanızın sağlık durumunun genel görünümünü sağlamak için toplanır. Bir orkestratör kullanıyorsanız, kümenin buna göre hareket edebilmesi için orkestratörkümenize sistem durumu bilgileri sağlayabilirsiniz. Uygulamanız için özelleştirilmiş yüksek kaliteli sağlık raporlamalarına yatırım yaparsanız, çalışan uygulamanız için sorunları çok daha kolay algılayabilir ve düzeltebilirsiniz.

## <a name="implement-health-checks-in-aspnet-core-services"></a>ASP.NET Core hizmetlerinde sağlık kontrolleri uygulayın

Bir ASP.NET Core microservice veya web uygulaması geliştirirken, ASP .NET Core 2.2[(Microsoft.Extensions.Diagnostics.HealthChecks)](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)bölümünde yayımlanan yerleşik sistem durumu denetimleri özelliğini kullanabilirsiniz. Birçok ASP.NET Core özellikleri gibi, sağlık kontrolleri hizmetleri ve bir ara bir dizi ile birlikte gelir.

Sistem durumu denetimi hizmetlerinin ve ara yazılımların kullanımı kolaydır ve uygulamanız için gerekli harici kaynağın (SQL Server veritabanı veya uzak API gibi) düzgün çalışıp çalışmadığını doğrulamanıza olanak sağlayan özellikler sağlar. Bu özelliği kullandığınızda, daha sonra açıkladığımız gibi kaynağın sağlıklı olmasının ne anlama geldiğini de belirleyebilirsiniz.

Bu özelliği etkin bir şekilde kullanmak için öncelikle mikro hizmetlerinizdeki hizmetleri yapılandırmanız gerekir. İkinci olarak, sistem durumu raporlarını sorgulayan bir ön uç uygulamasına ihtiyacınız vardır. Bu ön uç uygulaması özel bir raporlama uygulaması olabilir veya sağlık durumlarına göre tepki verebilecek bir orkestratör olabilir.

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a>Arka uç ASP.NET mikro hizmetlerinizde HealthChecks özelliğini kullanın

Bu bölümde, [Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) paketini kullanırken Core 3.1 Web API uygulamasında niçin healthchecks özelliğini ASP.NET öğreneceksiniz. Bu özelliğin eShopOnContainers gibi büyük ölçekli mikro hizmetlerde uygulanması sonraki bölümde açıklanmıştır.

Başlamak için, her microservice için sağlıklı bir durum oluşturan ne tanımlamak gerekir. Örnek uygulamada, API'sine HTTP üzerinden erişilebiliyorsa ve ilgili SQL Server veritabanı da mevcutsa mikrohizmetin sağlıklı olduğunu tanımlıyoruz.

.NET Core 3.1'de, yerleşik API'lerle hizmetleri yapılandırabilir, mikro hizmet ve bağımlı SQL Server veritabanı için bir Sistem Durumu Denetimi ekleyebilirsiniz:

```csharp
// Startup.cs from .NET Core 3.1 Web API sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
        // Add a health check for a SQL Server database
        .AddCheck(
            "OrderingDB-check",
            new SqlConnectionHealthCheck(Configuration["ConnectionString"]),
            HealthStatus.Unhealthy,
            new string[] { "orderingdb" });
}
```

Önceki kodda, `services.AddHealthChecks()` yöntem "Sağlıklı" ile bir durum kodu **200** döndürür temel bir HTTP denetimi yapılandırır.  Ayrıca, `AddCheck()` uzantı yöntemi, `SqlConnectionHealthCheck` ilgili SQL Veritabanı'nın sistem durumunu denetleyen bir özel yapılandırır.

Yöntem, `AddCheck()` belirtilen bir ada ve tür `IHealthCheck`uygulaması ile yeni bir sistem durumu denetimi ekler. AddCheck yöntemini kullanarak birden çok Sistem Durumu Denetimi ekleyebilirsiniz, böylece bir microservice tüm denetimleri sağlıklı olana kadar "sağlıklı" bir durum sağlamaz.

`SqlConnectionHealthCheck`bir bağlantı dizesini `IHealthCheck`oluşturucu parametre olarak alan ve SQL veritabanına bağlantının başarılı olup olmadığını denetlemek için basit bir sorgu yürüten özel bir sınıftır. Sorgu `HealthCheckResult.Healthy()` başarıyla yürütülür ve `FailureStatus` başarısız olduğunda gerçek bir özel durum ile döndürür.

```csharp
// Sample SQL Connection Health Check
public class SqlConnectionHealthCheck : IHealthCheck
{
    private static readonly string DefaultTestQuery = "Select 1";

    public string ConnectionString { get; }

    public string TestQuery { get; }

    public SqlConnectionHealthCheck(string connectionString)
        : this(connectionString, testQuery: DefaultTestQuery)
    {
    }

    public SqlConnectionHealthCheck(string connectionString, string testQuery)
    {
        ConnectionString = connectionString ?? throw new ArgumentNullException(nameof(connectionString));
        TestQuery = testQuery;
    }

    public async Task<HealthCheckResult> CheckHealthAsync(HealthCheckContext context, CancellationToken cancellationToken = default(CancellationToken))
    {
        using (var connection = new SqlConnection(ConnectionString))
        {
            try
            {
                await connection.OpenAsync(cancellationToken);

                if (TestQuery != null)
                {
                    var command = connection.CreateCommand();
                    command.CommandText = TestQuery;

                    await command.ExecuteNonQueryAsync(cancellationToken);
                }
            }
            catch (DbException ex)
            {
                return new HealthCheckResult(status: context.Registration.FailureStatus, exception: ex);
            }
        }

        return HealthCheckResult.Healthy();
    }
}
```

Önceki kodda, `Select 1` veritabanının Sistem Durumu'nu denetlemek için kullanılan sorgu olduğunu unutmayın. Mikro hizmetlerinizin kullanılabilirliğini izlemek için, Kubernetes gibi orkestratörler mikro hizmetleri test etmek için istekler göndererek düzenli olarak sağlık kontrolleri gerçekleştirirler. Bu işlemlerin hızlı olması ve kaynakların daha yüksek kullanılmasına neden olması için veritabanı sorgularınızı verimli tutmanız önemlidir.

Son olarak, url yoluna `/hc`yanıt veren bir ara yazılım ekleyin:

```csharp
// Startup.cs from .NET Core 3.1 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
        endpoints.MapHealthChecks("/hc");
        //...
    });
    //…
}
```

Bitiş noktası `<yourmicroservice>/hc` çağrıldığında, Başlangıç sınıfında `AddHealthChecks()` yöntemde yapılandırılan tüm sistem durumu denetimlerini çalıştırAr ve sonucu gösterir.

### <a name="healthchecks-implementation-in-eshoponcontainers"></a>EShopOnContainers HealthChecks uygulaması

eShopOnContainers'daki microservices görevini yerine getirmek için birden fazla hizmete güvenir. Örneğin, eShopOnContainers'ın `Catalog.API` microservice'i Azure Blob Depolama, SQL Server ve RabbitMQ gibi birçok hizmete bağlıdır. Bu nedenle, yöntem kullanılarak eklenen `AddCheck()` birkaç sistem durumu denetimleri vardır. Her bağımlı hizmet için, ilgili sistem durumunu tanımlayan özel `IHealthCheck` bir uygulamanın eklenmesi gerekir.

Açık kaynak projesi [AspNetCore.Diagnostics.HealthChecks,](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) .NET Core 3.1'in üzerine inşa edilen bu kurumsal hizmetlerin her biri için özel sağlık denetimi uygulamaları sağlayarak bu sorunu çözer. Her sağlık kontrolü, projeye kolayca eklenebilen tek bir NuGet paketi olarak kullanılabilir. eShopOnContainers tüm mikro hizmetlerde yoğun olarak kullanır.

Örneğin, `Catalog.API` microservice, aşağıdaki NuGet paketleri eklendi:

![AspNetCore.Diagnostics.HealthChecks NuGet paketlerinin ekran görüntüsü.](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

**Şekil 8-7**. AspNetCore.Diagnostics.HealthChecks kullanılarak Catalog.API'de uygulanan Özel Sağlık Kontrolleri

Aşağıdaki kodda, sistem durumu denetimi uygulamaları her bağımlı hizmet için eklenir ve sonra ara yazılım yapılandırılır:

```csharp
// Startup.cs from Catalog.api microservice
//
public static IServiceCollection AddCustomHealthCheck(this IServiceCollection services, IConfiguration configuration)
{
    var accountName = configuration.GetValue<string>("AzureStorageAccountName");
    var accountKey = configuration.GetValue<string>("AzureStorageAccountKey");

    var hcBuilder = services.AddHealthChecks();

    hcBuilder
        .AddSqlServer(
            configuration["ConnectionString"],
            name: "CatalogDB-check",
            tags: new string[] { "catalogdb" });

    if (!string.IsNullOrEmpty(accountName) && !string.IsNullOrEmpty(accountKey))
    {
        hcBuilder
            .AddAzureBlobStorage(
                $"DefaultEndpointsProtocol=https;AccountName={accountName};AccountKey={accountKey};EndpointSuffix=core.windows.net",
                name: "catalog-storage-check",
                tags: new string[] { "catalogstorage" });
    }
    if (configuration.GetValue<bool>("AzureServiceBusEnabled"))
    {
        hcBuilder
            .AddAzureServiceBusTopic(
                configuration["EventBusConnection"],
                topicName: "eshop_event_bus",
                name: "catalog-servicebus-check",
                tags: new string[] { "servicebus" });
    }
    else
    {
        hcBuilder
            .AddRabbitMQ(
                $"amqp://{configuration["EventBusConnection"]}",
                name: "catalog-rabbitmqbus-check",
                tags: new string[] { "rabbitmqbus" });
    }

    return services;
}
```

Son olarak, "/hc" bitiş noktasını dinlemek için HealthCheck ara yazılımını ekleyin:

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Mikro hizmetlerinizi sağlık durumları hakkında rapor vermek için sorgula

Bu makalede açıklandığı gibi sistem durumu denetimlerini yapılandırdığınızda ve Docker'da çalışan mikro hizmet varsa, sağlıklı olup olmadığını doğrudan bir tarayıcıdan kontrol edebilirsiniz. Konteyner bağlantı noktasını Docker ana bilgisayarında yayımlamanız gerekir, böylece eksternal `localhost`Docker ana bilgisayarı IP'den veya şekil 8-8'de gösterildiği gibi, konteynere erişebilirsiniz.

![JSON yanıtının ekran görüntüsü bir sağlık kontrolü yle döndürülür.](./media/monitor-app-health/health-check-json-response.png)

**Şekil 8-8**. Tarayıcıdan tek bir hizmetin sistem durumu durumunu denetleme

Bu testte, `Catalog.API` mikro hizmetin (bağlantı noktası 5101'de çalışan) sağlıklı olduğunu ve HTTP durum 200'ü ve JSON'daki durum bilgilerini döndürerek görebilirsiniz. Hizmet ayrıca SQL Server veritabanı bağımlılığı ve RabbitMQ sağlık kontrol, böylece sağlık kontrolü sağlıklı olarak kendini bildirdi.

## <a name="use-watchdogs"></a>Watchdogs kullanın

İzleme örgütü, hizmetler arasında sağlık ve yük izleyebilen ve daha önce tanıtılan `HealthChecks` kitaplıkla sorgulayarak mikro hizmetler hakkında sağlık raporu bildirebilen ayrı bir hizmettir. Bu, tek bir hizmetin görünümüne dayalı olarak algılanmayacak hataları önlemeye yardımcı olabilir. Watchdogs da kullanıcı etkileşimi olmadan bilinen koşullar için düzeltme eylemleri gerçekleştirebilirsiniz kod barındırmak için iyi bir yerdir.

eShopOnContainers örneği, Şekil 8-9'da gösterildiği gibi örnek sağlık kontrol raporlarını görüntüleyen bir web sayfası içerir. Bu sadece eShopOnContainers mikrohizmetler ve web uygulamaları nın durumunu gösterir beri sahip olabileceğiniz en basit watchdog olduğunu. Genellikle bir watchdog da sağlıksız durumları algılar eylemleri alır.

Neyse ki, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) da yapılandırılan URI'lerden sağlık kontrol sonuçlarını görüntülemek için kullanılabilecek [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet paketi sağlar.

![Sağlık Kontrolleri UI eShopOnContainers sağlık durumları Ekran görüntüsü.](./media/monitor-app-health/health-check-status-ui.png)

**Şekil 8-9**. örnek sağlık kontrol raporu eShopOnContainers

Özetle, bu izleme hizmeti her microservice'in "/hc" bitiş noktasını sorgular. Bu, içinde tanımlanan tüm sağlık denetimlerini yürütecek ve tüm bu denetimlere bağlı olarak genel bir sağlık durumu döndürecektir. HealthChecksUI watchdog hizmetinin Startup.cs eklenmesi gereken birkaç yapılandırma girişleri ve iki kod satırı ile tüketmek kolaydır.

Sistem durumu denetimi ui için örnek yapılandırma dosyası:

```json
// Configuration
{
  "HealthChecks-UI": {
    "HealthChecks": [
      {
        "Name": "Ordering HTTP Check",
        "Uri": "http://localhost:5102/hc"
      },
      {
        "Name": "Ordering HTTP Background Check",
        "Uri": "http://localhost:5111/hc"
      },
      //...
    ]}
}
```

HealthChecksUI ekler Startup.cs dosyası:

```csharp
// Startup.cs from WebStatus(Watch Dog) service
//
public void ConfigureServices(IServiceCollection services)
{
    //…
    // Registers required services for health checks
    services.AddHealthChecksUI();
}
//…
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecksUI(config=> config.UIPath = “/hc-ui”);
    //…
}
```

## <a name="health-checks-when-using-orchestrators"></a>Orkestratörleri kullanırken sistem durumu kontrolleri

Mikro hizmetlerinizin kullanılabilirliğini izlemek için, Kubernetes ve Service Fabric gibi orkestratörler, mikro hizmetleri test etmek için istekler göndererek düzenli olarak sağlık kontrolleri gerçekleştirirler. Bir orkestratör bir hizmetin/kapsayıcının sağlıksız olduğunu belirlediğinde, istekleri o örne yönlendirmeyi durdurur. Ayrıca genellikle bu kapsayıcının yeni bir örneğini oluşturur.

Örneğin, çoğu orkestratör, sıfır kapalı kalma süresi dağıtımlarını yönetmek için sistem durumu denetimlerini kullanabilir. Yalnızca bir hizmetin/kapsayıcının durumu sağlıklı olduğunda, orkestratör trafiği servis/konteyner örneklerine yönlendirmeye başlar.

Bir orkestratör bir uygulama yükseltmesi yaptığında sistem durumu izleme özellikle önemlidir. Bazı orkestratörler (Azure Hizmet Dokusu gibi) hizmetleri aşamalı olarak günceller(örneğin, her uygulama yükseltmesi için küme yüzeyinin beşte birini güncelleyebilirler). Aynı anda yükseltilen düğüm *kümesine yükseltme etki alanı*denir. Her yükseltme etki alanı yükseltildikten ve kullanıcılar tarafından kullanılabilir hale geldikten sonra, dağıtım bir sonraki yükseltme etki alanına geçmeden önce yükseltme etki alanının sistem durumu denetimlerinden geçmesi gerekir.

Hizmet sağlığının bir diğer yönü de hizmetten ölçümleri raporlamaktır. Bu, Service Fabric gibi bazı orkestratörlerin sağlık modelinin gelişmiş bir yeteneğidir. Kaynak kullanımını dengelemek için kullanıldığından, ölçümler bir orkestratör kullanırken önemlidir. Ölçümler de sistem sağlığının bir göstergesi olabilir. Örneğin, çok sayıda mikro hizmeti olan bir uygulamanız olabilir ve her örnek saniyede istek (RPS) ölçümü bildiriyor. Bir hizmet başka bir hizmetten daha fazla kaynak (bellek, işlemci, vb.) kullanıyorsa, orkestratör, kaynak kullanımını bile sürdürmeye çalışmak için hizmet örneklerini kümede taşıyabilir.

Azure Hizmet Kumaşı'nın basit sistem durumu kontrollerinden daha gelişmiş olan kendi [Sistem Durumu İzleme modelini](/azure/service-fabric/service-fabric-health-introduction)sağladığını unutmayın.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Gelişmiş izleme: görselleştirme, analiz ve uyarılar

İzlemenin son bölümü olay akışını görselleştirmek, hizmet performansı hakkında raporlama ve bir sorun algılandığında uyarı vermektir. İzlemenin bu yönü için farklı çözümler kullanabilirsiniz.

[AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks)açıklarken gösterilen özel sayfa gibi, hizmetlerinizin durumunu gösteren basit özel uygulamalar kullanabilirsiniz. Veya etkinlik akışına dayalı uyarıları yükseltmek için [Azure Monitor](https://azure.microsoft.com/services/monitor/) gibi daha gelişmiş araçları kullanabilirsiniz.

Son olarak, tüm olay akışlarını depolıyorsanız, verileri görselleştirmek için Microsoft Power BI veya Kibana veya Splunk gibi diğer çözümleri kullanabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET Core için HealthChecks ve HealthChecks UI** \
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- **Hizmet Kumaş sağlık izleme giriş** \
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- **Azure Monitör** \
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
>[Önceki](implement-circuit-breaker-pattern.md)
>[Sonraki](../secure-net-microservices-web-applications/index.md)
