---
title: Sistem durumunu izleme
description: Sağlık izleme uygulamanın bir yolunu keşfedin.
ms.date: 03/02/2020
ms.openlocfilehash: 88354ae0ae59dbfbe40dbe1b25320f8f93d042ce
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988862"
---
# <a name="health-monitoring"></a><span data-ttu-id="9a216-103">Sistem durumunu izleme</span><span class="sxs-lookup"><span data-stu-id="9a216-103">Health monitoring</span></span>

<span data-ttu-id="9a216-104">Sistem durumu izleme, konteynerlerinizin ve mikro hizmetlerinizin durumu hakkında neredeyse gerçek zamanlı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a216-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="9a216-105">Sağlık izleme, mikro hizmetlerin işletiminin birçok yönü için önemlidir ve daha sonra açıklandığı gibi, orkestratörlerin aşamalı olarak kısmi uygulama yükseltmeleri gerçekleştirmeleri özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9a216-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="9a216-106">Mikro hizmetler tabanlı uygulamalar, performans monitörlerini, zamanlayıcılarını ve orkestratörlerini çok sayıda hizmeti izlemek için genellikle sinyal veya sistem durumu denetimlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a216-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="9a216-107">Hizmetler isteğe bağlı olarak veya bir zamanlamada bir tür "Yaşıyorum" sinyali gönderemiyorsa, güncelleştirmeleri dağıttığınızda uygulamanız risklerle karşı karşıya kalabilir veya hataları çok geç algılayabilir ve büyük kesintilere neden olabilecek basamaklı arızaları durduramayabilir.</span><span class="sxs-lookup"><span data-stu-id="9a216-107">If services cannot send some sort of "I'm alive" signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="9a216-108">Tipik modelde, hizmetler durumları hakkında raporlar gönderir ve bu bilgiler, uygulamanızın sağlık durumunun genel görünümünü sağlamak için toplanır.</span><span class="sxs-lookup"><span data-stu-id="9a216-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="9a216-109">Bir orkestratör kullanıyorsanız, kümenin buna göre hareket edebilmesi için orkestratörkümenize sistem durumu bilgileri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a216-109">If you're using an orchestrator, you can provide health information to your orchestrator's cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="9a216-110">Uygulamanız için özelleştirilmiş yüksek kaliteli sağlık raporlamalarına yatırım yaparsanız, çalışan uygulamanız için sorunları çok daha kolay algılayabilir ve düzeltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a216-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="9a216-111">ASP.NET Core hizmetlerinde sağlık kontrolleri uygulayın</span><span class="sxs-lookup"><span data-stu-id="9a216-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="9a216-112">Bir ASP.NET Core microservice veya web uygulaması geliştirirken, ASP .NET Core 2.2[(Microsoft.Extensions.Diagnostics.HealthChecks)](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)bölümünde yayımlanan yerleşik sistem durumu denetimleri özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a216-112">When developing an ASP.NET Core microservice or web application, you can use the built-in health checks feature that was released in ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)).</span></span> <span data-ttu-id="9a216-113">Birçok ASP.NET Core özellikleri gibi, sağlık kontrolleri hizmetleri ve bir ara bir dizi ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="9a216-113">Like many ASP.NET Core features, health checks come with a set of services and a middleware.</span></span>

<span data-ttu-id="9a216-114">Sistem durumu denetimi hizmetlerinin ve ara yazılımların kullanımı kolaydır ve uygulamanız için gerekli harici kaynağın (SQL Server veritabanı veya uzak API gibi) düzgün çalışıp çalışmadığını doğrulamanıza olanak sağlayan özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a216-114">Health check services and middleware are easy to use and provide capabilities that let you validate if any external resource needed for your application (like a SQL Server database or a remote API) is working properly.</span></span> <span data-ttu-id="9a216-115">Bu özelliği kullandığınızda, daha sonra açıkladığımız gibi kaynağın sağlıklı olmasının ne anlama geldiğini de belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a216-115">When you use this feature, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="9a216-116">Bu özelliği etkin bir şekilde kullanmak için öncelikle mikro hizmetlerinizdeki hizmetleri yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a216-116">To use this feature effectively, you need to first configure services in your microservices.</span></span> <span data-ttu-id="9a216-117">İkinci olarak, sistem durumu raporlarını sorgulayan bir ön uç uygulamasına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="9a216-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="9a216-118">Bu ön uç uygulaması özel bir raporlama uygulaması olabilir veya sağlık durumlarına göre tepki verebilecek bir orkestratör olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a216-118">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="9a216-119">Arka uç ASP.NET mikro hizmetlerinizde HealthChecks özelliğini kullanın</span><span class="sxs-lookup"><span data-stu-id="9a216-119">Use the HealthChecks feature in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="9a216-120">Bu bölümde, [Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) paketini kullanırken Core 3.1 Web API uygulamasında niçin healthchecks özelliğini ASP.NET öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="9a216-120">In this section, you'll learn how to implement the HealthChecks feature in a sample ASP.NET Core 3.1 Web API application when using the [Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) package.</span></span> <span data-ttu-id="9a216-121">Bu özelliğin eShopOnContainers gibi büyük ölçekli mikro hizmetlerde uygulanması sonraki bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9a216-121">The Implementation of this feature in a large-scale microservices like the eShopOnContainers is explained in the next section.</span></span>

<span data-ttu-id="9a216-122">Başlamak için, her microservice için sağlıklı bir durum oluşturan ne tanımlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a216-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="9a216-123">Örnek uygulamada, API'sine HTTP üzerinden erişilebiliyorsa ve ilgili SQL Server veritabanı da mevcutsa mikrohizmetin sağlıklı olduğunu tanımlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="9a216-123">In the sample application, we define the microservice is healthy if its API is accessible via HTTP and its related SQL Server database is also available.</span></span>

<span data-ttu-id="9a216-124">.NET Core 3.1'de, yerleşik API'lerle hizmetleri yapılandırabilir, mikro hizmet ve bağımlı SQL Server veritabanı için bir Sistem Durumu Denetimi ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9a216-124">In .NET Core 3.1, with the built-in APIs, you can configure the services, add a Health Check for the microservice and its dependent SQL Server database in this way:</span></span>

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

<span data-ttu-id="9a216-125">Önceki kodda, `services.AddHealthChecks()` yöntem "Sağlıklı" ile bir durum kodu **200** döndürür temel bir HTTP denetimi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9a216-125">In the previous code, the `services.AddHealthChecks()` method configures a basic HTTP check that returns a status code **200** with "Healthy".</span></span>  <span data-ttu-id="9a216-126">Ayrıca, `AddCheck()` uzantı yöntemi, `SqlConnectionHealthCheck` ilgili SQL Veritabanı'nın sistem durumunu denetleyen bir özel yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9a216-126">Further, the `AddCheck()` extension method configures a custom `SqlConnectionHealthCheck` that checks the related SQL Database's health.</span></span>

<span data-ttu-id="9a216-127">Yöntem, `AddCheck()` belirtilen bir ada ve tür `IHealthCheck`uygulaması ile yeni bir sistem durumu denetimi ekler.</span><span class="sxs-lookup"><span data-stu-id="9a216-127">The `AddCheck()` method adds a new health check with a specified name and the implementation of type `IHealthCheck`.</span></span> <span data-ttu-id="9a216-128">AddCheck yöntemini kullanarak birden çok Sistem Durumu Denetimi ekleyebilirsiniz, böylece bir microservice tüm denetimleri sağlıklı olana kadar "sağlıklı" bir durum sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="9a216-128">You can add multiple Health Checks using AddCheck method, so a microservice won't provide a "healthy" status until all its checks are healthy.</span></span>

<span data-ttu-id="9a216-129">`SqlConnectionHealthCheck`bir bağlantı dizesini `IHealthCheck`oluşturucu parametre olarak alan ve SQL veritabanına bağlantının başarılı olup olmadığını denetlemek için basit bir sorgu yürüten özel bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="9a216-129">`SqlConnectionHealthCheck` is a custom class that implements `IHealthCheck`, which takes a connection string as a constructor parameter and executes a simple query to check if the connection to the SQL database is successful.</span></span> <span data-ttu-id="9a216-130">Sorgu `HealthCheckResult.Healthy()` başarıyla yürütülür ve `FailureStatus` başarısız olduğunda gerçek bir özel durum ile döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a216-130">It returns `HealthCheckResult.Healthy()` if the query was executed successfully and a `FailureStatus` with the actual exception when it fails.</span></span>

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

<span data-ttu-id="9a216-131">Önceki kodda, `Select 1` veritabanının Sistem Durumu'nu denetlemek için kullanılan sorgu olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9a216-131">Note that in the previous code, `Select 1` is the query used to check the Health of the database.</span></span> <span data-ttu-id="9a216-132">Mikro hizmetlerinizin kullanılabilirliğini izlemek için, Kubernetes gibi orkestratörler mikro hizmetleri test etmek için istekler göndererek düzenli olarak sağlık kontrolleri gerçekleştirirler.</span><span class="sxs-lookup"><span data-stu-id="9a216-132">To monitor the availability of your microservices, orchestrators like Kubernetes periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="9a216-133">Bu işlemlerin hızlı olması ve kaynakların daha yüksek kullanılmasına neden olması için veritabanı sorgularınızı verimli tutmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9a216-133">It's important to keep your database queries efficient so that these operations are quick and don’t result in a higher utilization of resources.</span></span>

<span data-ttu-id="9a216-134">Son olarak, url yoluna `/hc`yanıt veren bir ara yazılım ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9a216-134">Finally, add a middleware that responds to the url path `/hc`:</span></span>

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

<span data-ttu-id="9a216-135">Bitiş noktası `<yourmicroservice>/hc` çağrıldığında, Başlangıç sınıfında `AddHealthChecks()` yöntemde yapılandırılan tüm sistem durumu denetimlerini çalıştırAr ve sonucu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a216-135">When the endpoint `<yourmicroservice>/hc` is invoked, it runs all the health checks that are configured in the `AddHealthChecks()` method in the Startup class and shows the result.</span></span>

### <a name="healthchecks-implementation-in-eshoponcontainers"></a><span data-ttu-id="9a216-136">EShopOnContainers HealthChecks uygulaması</span><span class="sxs-lookup"><span data-stu-id="9a216-136">HealthChecks implementation in eShopOnContainers</span></span>

<span data-ttu-id="9a216-137">eShopOnContainers'daki microservices görevini yerine getirmek için birden fazla hizmete güvenir.</span><span class="sxs-lookup"><span data-stu-id="9a216-137">Microservices in eShopOnContainers rely on multiple services to perform its task.</span></span> <span data-ttu-id="9a216-138">Örneğin, eShopOnContainers'ın `Catalog.API` microservice'i Azure Blob Depolama, SQL Server ve RabbitMQ gibi birçok hizmete bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9a216-138">For example, the `Catalog.API` microservice from eShopOnContainers depends on many services, such as Azure Blob Storage, SQL Server, and RabbitMQ.</span></span> <span data-ttu-id="9a216-139">Bu nedenle, yöntem kullanılarak eklenen `AddCheck()` birkaç sistem durumu denetimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="9a216-139">Therefore, it has several health checks added using the `AddCheck()` method.</span></span> <span data-ttu-id="9a216-140">Her bağımlı hizmet için, ilgili sistem durumunu tanımlayan özel `IHealthCheck` bir uygulamanın eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a216-140">For every dependent service, a custom `IHealthCheck` implementation that defines its respective health status would need to be added.</span></span>

<span data-ttu-id="9a216-141">Açık kaynak projesi [AspNetCore.Diagnostics.HealthChecks,](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) .NET Core 3.1'in üzerine inşa edilen bu kurumsal hizmetlerin her biri için özel sağlık denetimi uygulamaları sağlayarak bu sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="9a216-141">The open-source project [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) solves this problem by providing custom health check implementations for each of these enterprise services, that are built on top of .NET Core 3.1.</span></span> <span data-ttu-id="9a216-142">Her sağlık kontrolü, projeye kolayca eklenebilen tek bir NuGet paketi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9a216-142">Each health check is available as an individual NuGet package that can be easily added to the project.</span></span> <span data-ttu-id="9a216-143">eShopOnContainers tüm mikro hizmetlerde yoğun olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a216-143">eShopOnContainers uses them extensively in all its microservices.</span></span>

<span data-ttu-id="9a216-144">Örneğin, `Catalog.API` microservice, aşağıdaki NuGet paketleri eklendi:</span><span class="sxs-lookup"><span data-stu-id="9a216-144">For instance, in the `Catalog.API` microservice, the following NuGet packages were added:</span></span>

![AspNetCore.Diagnostics.HealthChecks NuGet paketlerinin ekran görüntüsü.](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

<span data-ttu-id="9a216-146">**Şekil 8-7**.</span><span class="sxs-lookup"><span data-stu-id="9a216-146">**Figure 8-7**.</span></span> <span data-ttu-id="9a216-147">AspNetCore.Diagnostics.HealthChecks kullanılarak Catalog.API'de uygulanan Özel Sağlık Kontrolleri</span><span class="sxs-lookup"><span data-stu-id="9a216-147">Custom Health Checks implemented in Catalog.API using AspNetCore.Diagnostics.HealthChecks</span></span>

<span data-ttu-id="9a216-148">Aşağıdaki kodda, sistem durumu denetimi uygulamaları her bağımlı hizmet için eklenir ve sonra ara yazılım yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="9a216-148">In the following code, the health check implementations are added for each dependent service and then the middleware is configured:</span></span>

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

<span data-ttu-id="9a216-149">Son olarak, "/hc" bitiş noktasını dinlemek için HealthCheck ara yazılımını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9a216-149">Finally, add the HealthCheck middleware to listen to “/hc” endpoint:</span></span>

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="9a216-150">Mikro hizmetlerinizi sağlık durumları hakkında rapor vermek için sorgula</span><span class="sxs-lookup"><span data-stu-id="9a216-150">Query your microservices to report about their health status</span></span>

<span data-ttu-id="9a216-151">Bu makalede açıklandığı gibi sistem durumu denetimlerini yapılandırdığınızda ve Docker'da çalışan mikro hizmet varsa, sağlıklı olup olmadığını doğrudan bir tarayıcıdan kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a216-151">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span> <span data-ttu-id="9a216-152">Konteyner bağlantı noktasını Docker ana bilgisayarında yayımlamanız gerekir, böylece eksternal `localhost`Docker ana bilgisayarı IP'den veya şekil 8-8'de gösterildiği gibi, konteynere erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a216-152">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![JSON yanıtının ekran görüntüsü bir sağlık kontrolü yle döndürülür.](./media/monitor-app-health/health-check-json-response.png)

<span data-ttu-id="9a216-154">**Şekil 8-8**.</span><span class="sxs-lookup"><span data-stu-id="9a216-154">**Figure 8-8**.</span></span> <span data-ttu-id="9a216-155">Tarayıcıdan tek bir hizmetin sistem durumu durumunu denetleme</span><span class="sxs-lookup"><span data-stu-id="9a216-155">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="9a216-156">Bu testte, `Catalog.API` mikro hizmetin (bağlantı noktası 5101'de çalışan) sağlıklı olduğunu ve HTTP durum 200'ü ve JSON'daki durum bilgilerini döndürerek görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a216-156">In that test, you can see that the `Catalog.API` microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="9a216-157">Hizmet ayrıca SQL Server veritabanı bağımlılığı ve RabbitMQ sağlık kontrol, böylece sağlık kontrolü sağlıklı olarak kendini bildirdi.</span><span class="sxs-lookup"><span data-stu-id="9a216-157">The service also checked the health of its SQL Server database dependency and RabbitMQ, so the health check reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="9a216-158">Watchdogs kullanın</span><span class="sxs-lookup"><span data-stu-id="9a216-158">Use watchdogs</span></span>

<span data-ttu-id="9a216-159">İzleme örgütü, hizmetler arasında sağlık ve yük izleyebilen ve daha önce tanıtılan `HealthChecks` kitaplıkla sorgulayarak mikro hizmetler hakkında sağlık raporu bildirebilen ayrı bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="9a216-159">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="9a216-160">Bu, tek bir hizmetin görünümüne dayalı olarak algılanmayacak hataları önlemeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a216-160">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="9a216-161">Watchdogs da kullanıcı etkileşimi olmadan bilinen koşullar için düzeltme eylemleri gerçekleştirebilirsiniz kod barındırmak için iyi bir yerdir.</span><span class="sxs-lookup"><span data-stu-id="9a216-161">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="9a216-162">eShopOnContainers örneği, Şekil 8-9'da gösterildiği gibi örnek sağlık kontrol raporlarını görüntüleyen bir web sayfası içerir.</span><span class="sxs-lookup"><span data-stu-id="9a216-162">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="9a216-163">Bu sadece eShopOnContainers mikrohizmetler ve web uygulamaları nın durumunu gösterir beri sahip olabileceğiniz en basit watchdog olduğunu.</span><span class="sxs-lookup"><span data-stu-id="9a216-163">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="9a216-164">Genellikle bir watchdog da sağlıksız durumları algılar eylemleri alır.</span><span class="sxs-lookup"><span data-stu-id="9a216-164">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

<span data-ttu-id="9a216-165">Neyse ki, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) da yapılandırılan URI'lerden sağlık kontrol sonuçlarını görüntülemek için kullanılabilecek [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet paketi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a216-165">Fortunately, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) also provides [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet package that can be used to display the health check results from the configured URIs.</span></span>

![Sağlık Kontrolleri UI eShopOnContainers sağlık durumları Ekran görüntüsü.](./media/monitor-app-health/health-check-status-ui.png)

<span data-ttu-id="9a216-167">**Şekil 8-9**.</span><span class="sxs-lookup"><span data-stu-id="9a216-167">**Figure 8-9**.</span></span> <span data-ttu-id="9a216-168">örnek sağlık kontrol raporu eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="9a216-168">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="9a216-169">Özetle, bu izleme hizmeti her microservice'in "/hc" bitiş noktasını sorgular.</span><span class="sxs-lookup"><span data-stu-id="9a216-169">In summary, this watchdog service queries each microservice's "/hc" endpoint.</span></span> <span data-ttu-id="9a216-170">Bu, içinde tanımlanan tüm sağlık denetimlerini yürütecek ve tüm bu denetimlere bağlı olarak genel bir sağlık durumu döndürecektir.</span><span class="sxs-lookup"><span data-stu-id="9a216-170">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span> <span data-ttu-id="9a216-171">HealthChecksUI watchdog hizmetinin Startup.cs eklenmesi gereken birkaç yapılandırma girişleri ve iki kod satırı ile tüketmek kolaydır.</span><span class="sxs-lookup"><span data-stu-id="9a216-171">The HealthChecksUI is easy to consume with a few configuration entries and two lines of code that needs to be added into the Startup.cs of the watchdog service.</span></span>

<span data-ttu-id="9a216-172">Sistem durumu denetimi ui için örnek yapılandırma dosyası:</span><span class="sxs-lookup"><span data-stu-id="9a216-172">Sample configuration file for health check UI:</span></span>

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

<span data-ttu-id="9a216-173">HealthChecksUI ekler Startup.cs dosyası:</span><span class="sxs-lookup"><span data-stu-id="9a216-173">Startup.cs file that adds HealthChecksUI:</span></span>

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
    app.UseHealthChecksUI(config=> config.UIPath = "/hc-ui");
    //…
}
```

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="9a216-174">Orkestratörleri kullanırken sistem durumu kontrolleri</span><span class="sxs-lookup"><span data-stu-id="9a216-174">Health checks when using orchestrators</span></span>

<span data-ttu-id="9a216-175">Mikro hizmetlerinizin kullanılabilirliğini izlemek için, Kubernetes ve Service Fabric gibi orkestratörler, mikro hizmetleri test etmek için istekler göndererek düzenli olarak sağlık kontrolleri gerçekleştirirler.</span><span class="sxs-lookup"><span data-stu-id="9a216-175">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="9a216-176">Bir orkestratör bir hizmetin/kapsayıcının sağlıksız olduğunu belirlediğinde, istekleri o örne yönlendirmeyi durdurur.</span><span class="sxs-lookup"><span data-stu-id="9a216-176">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="9a216-177">Ayrıca genellikle bu kapsayıcının yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a216-177">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="9a216-178">Örneğin, çoğu orkestratör, sıfır kapalı kalma süresi dağıtımlarını yönetmek için sistem durumu denetimlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="9a216-178">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="9a216-179">Yalnızca bir hizmetin/kapsayıcının durumu sağlıklı olduğunda, orkestratör trafiği servis/konteyner örneklerine yönlendirmeye başlar.</span><span class="sxs-lookup"><span data-stu-id="9a216-179">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="9a216-180">Bir orkestratör bir uygulama yükseltmesi yaptığında sistem durumu izleme özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9a216-180">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="9a216-181">Bazı orkestratörler (Azure Hizmet Dokusu gibi) hizmetleri aşamalı olarak günceller(örneğin, her uygulama yükseltmesi için küme yüzeyinin beşte birini güncelleyebilirler).</span><span class="sxs-lookup"><span data-stu-id="9a216-181">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="9a216-182">Aynı anda yükseltilen düğüm *kümesine yükseltme etki alanı*denir.</span><span class="sxs-lookup"><span data-stu-id="9a216-182">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="9a216-183">Her yükseltme etki alanı yükseltildikten ve kullanıcılar tarafından kullanılabilir hale geldikten sonra, dağıtım bir sonraki yükseltme etki alanına geçmeden önce yükseltme etki alanının sistem durumu denetimlerinden geçmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a216-183">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="9a216-184">Hizmet sağlığının bir diğer yönü de hizmetten ölçümleri raporlamaktır.</span><span class="sxs-lookup"><span data-stu-id="9a216-184">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="9a216-185">Bu, Service Fabric gibi bazı orkestratörlerin sağlık modelinin gelişmiş bir yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="9a216-185">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="9a216-186">Kaynak kullanımını dengelemek için kullanıldığından, ölçümler bir orkestratör kullanırken önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9a216-186">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="9a216-187">Ölçümler de sistem sağlığının bir göstergesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a216-187">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="9a216-188">Örneğin, çok sayıda mikro hizmeti olan bir uygulamanız olabilir ve her örnek saniyede istek (RPS) ölçümü bildiriyor.</span><span class="sxs-lookup"><span data-stu-id="9a216-188">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="9a216-189">Bir hizmet başka bir hizmetten daha fazla kaynak (bellek, işlemci, vb.) kullanıyorsa, orkestratör, kaynak kullanımını bile sürdürmeye çalışmak için hizmet örneklerini kümede taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="9a216-189">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="9a216-190">Azure Hizmet Kumaşı'nın basit sistem durumu kontrollerinden daha gelişmiş olan kendi [Sistem Durumu İzleme modelini](/azure/service-fabric/service-fabric-health-introduction)sağladığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9a216-190">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="9a216-191">Gelişmiş izleme: görselleştirme, analiz ve uyarılar</span><span class="sxs-lookup"><span data-stu-id="9a216-191">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="9a216-192">İzlemenin son bölümü olay akışını görselleştirmek, hizmet performansı hakkında raporlama ve bir sorun algılandığında uyarı vermektir.</span><span class="sxs-lookup"><span data-stu-id="9a216-192">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="9a216-193">İzlemenin bu yönü için farklı çözümler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a216-193">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="9a216-194">[AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks)açıklarken gösterilen özel sayfa gibi, hizmetlerinizin durumunu gösteren basit özel uygulamalar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a216-194">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span></span> <span data-ttu-id="9a216-195">Veya etkinlik akışına dayalı uyarıları yükseltmek için [Azure Monitor](https://azure.microsoft.com/services/monitor/) gibi daha gelişmiş araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a216-195">Or you could use more advanced tools like [Azure Monitor](https://azure.microsoft.com/services/monitor/) to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="9a216-196">Son olarak, tüm olay akışlarını depolıyorsanız, verileri görselleştirmek için Microsoft Power BI veya Kibana veya Splunk gibi diğer çözümleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a216-196">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9a216-197">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="9a216-197">Additional resources</span></span>

- <span data-ttu-id="9a216-198">**ASP.NET Core için HealthChecks ve HealthChecks UI** </span><span class="sxs-lookup"><span data-stu-id="9a216-198">**HealthChecks and HealthChecks UI for ASP.NET Core** </span></span>\
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- <span data-ttu-id="9a216-199">**Hizmet Kumaş sağlık izleme giriş** </span><span class="sxs-lookup"><span data-stu-id="9a216-199">**Introduction to Service Fabric health monitoring** </span></span>\
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="9a216-200">**Azure Monitör** </span><span class="sxs-lookup"><span data-stu-id="9a216-200">**Azure Monitor** </span></span>\
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
><span data-ttu-id="9a216-201">[Önceki](implement-circuit-breaker-pattern.md)
>[Sonraki](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="9a216-201">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>
