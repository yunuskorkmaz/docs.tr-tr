---
title: Sistem durumu izleme
description: Sistem durumu izlemeyi uygulamayla bir yolu bulun.
ms.date: 01/07/2019
ms.openlocfilehash: f1d63e04bbea95fcf0a9f9d3b50aef0e7d4a830e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732868"
---
# <a name="health-monitoring"></a><span data-ttu-id="08843-103">Sistem durumu izleme</span><span class="sxs-lookup"><span data-stu-id="08843-103">Health monitoring</span></span>

<span data-ttu-id="08843-104">Sistem durumu izleme, kapsayıcılarınızın ve mikro hizmetlerinizin durumu hakkında neredeyse gerçek zamanlı bilgilere izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="08843-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="08843-105">Sistem durumu izleme, işletim mikro hizmetlerinin birden çok yönü için kritik öneme sahiptir ve bu, daha sonra açıklandığı gibi, bazı durumlarda, aşamalar halinde kısmi uygulama yükseltmeleri gerçekleştirirken özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="08843-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="08843-106">Mikro hizmet tabanlı uygulamalar genellikle performans izleyicilerinin, zamanlayıcılar ve düzenleyicilerin çok sayıda hizmeti izlemesini sağlamak için sinyal veya sistem durumu denetimleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="08843-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="08843-107">Hizmetler, istek üzerine veya bir zamanlamaya göre bir miktar "canlım" sinyali gönderebiliyorsa, güncelleştirmeleri dağıtırken uygulamanız risk altında olabilir veya yalnızca çok geç olan sorunları algılayabilir ve büyük kesintilerde ortaya çıkabilecek basamaklı sorunları durduramaz.</span><span class="sxs-lookup"><span data-stu-id="08843-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="08843-108">Tipik modelde, hizmetler durumları hakkında raporlar gönderir ve uygulamanızın sistem durumu durumunun genel bir görünümünü sağlamak için bu bilgiler toplanır.</span><span class="sxs-lookup"><span data-stu-id="08843-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="08843-109">Orchestrator kullanıyorsanız, kümenin uygun şekilde davranabilmesi için Orchestrator kümesine sistem durumu bilgileri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08843-109">If you're using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="08843-110">Uygulamanız için özelleştirilmiş yüksek kaliteli sistem durumu raporlaması yatırdığınızda, çalışan uygulamanızın sorunlarını daha kolay algılayabilir ve giderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08843-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="08843-111">ASP.NET Core hizmetlerinde sistem durumu denetimleri uygulama</span><span class="sxs-lookup"><span data-stu-id="08843-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="08843-112">ASP.NET Core mikro hizmet veya Web uygulaması geliştirirken, ASP .NET Core 2,2 ' de yayınlanan yerleşik sistem durumu denetimleri özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08843-112">When developing an ASP.NET Core microservice or web application, you can use the built-in health checks feature that was released in ASP .NET Core 2.2.</span></span> <span data-ttu-id="08843-113">Birçok ASP.NET Core özelliği gibi, sistem durumu denetimleri de bir dizi hizmet ve bir ara yazılım ile gelir.</span><span class="sxs-lookup"><span data-stu-id="08843-113">Like many ASP.NET Core features, health checks come with a set of services and a middleware.</span></span>

<span data-ttu-id="08843-114">Sistem durumu denetimi Hizmetleri ve ara yazılımı kullanımı kolaydır ve uygulamanız için gerekli herhangi bir dış kaynak (SQL Server veritabanı veya uzak bir API gibi) düzgün çalışıp çalışmadığını doğrulamanıza olanak sağlayan yetenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="08843-114">Health check services and middleware are easy to use and provide capabilities that let you validate if any external resource needed for your application (like a SQL Server database or a remote API) is working properly.</span></span> <span data-ttu-id="08843-115">Bu özelliği kullandığınızda, daha sonra açıklandığımız için kaynağın sağlıklı ne anlama geldiğini de seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08843-115">When you use this feature, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="08843-116">Bu özelliği etkin bir şekilde kullanmak için, önce mikro hizmetinizdeki hizmetleri yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="08843-116">To use this feature effectively, you need to first configure services in your microservices.</span></span> <span data-ttu-id="08843-117">İkincisi, sistem durumu raporlarını sorgulayan bir ön uç uygulamasına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="08843-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="08843-118">Bu ön uç uygulama özel bir raporlama uygulaması olabilir veya sistem durumu durumlarına göre tepki verebilecek bir Orchestrator 'ın kendisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="08843-118">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="08843-119">Arka uç ASP.NET mikro hizmetlerinizin Healthdenetimleri özelliğini kullanın</span><span class="sxs-lookup"><span data-stu-id="08843-119">Use the HealthChecks feature in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="08843-120">Bu bölümde, Healthdenetimleri özelliğinin örnek bir ASP.NET Core 2,2 Web API uygulamasında nasıl kullanıldığını öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="08843-120">In this section, you will learn how the HealthChecks feature is used in a sample ASP.NET Core 2.2 Web API application.</span></span> <span data-ttu-id="08843-121">EShopOnContainers gibi büyük ölçekli mikro hizmetlerde bu özelliğin uygulanması, sonraki bölümde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="08843-121">Implementation of this feature in a large scale microservices like the eShopOnContainers is explained in the later section.</span></span> <span data-ttu-id="08843-122">Başlamak için, her mikro hizmet için sağlıklı durumu neyin oluşturduğunu tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="08843-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="08843-123">Örnek uygulamada, mikro hizmet API 'sine HTTP üzerinden erişilebiliyorsa ve ilgili SQL Server veritabanı da kullanılabilir olduğunda mikro hizmetler sağlıklı olur.</span><span class="sxs-lookup"><span data-stu-id="08843-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and its related SQL Server database is also available.</span></span>

<span data-ttu-id="08843-124">.NET Core 2,2 ' de, yerleşik API 'Ler ile hizmetleri yapılandırabilir, mikro hizmet için bir sistem durumu denetimi ve bu şekilde bağımlı SQL Server veritabanı ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="08843-124">In .NET Core 2.2, with the built-in APIs, you can configure the services, add a Health Check for the microservice and its dependent SQL Server database in this way:</span></span>

```csharp
// Startup.cs from .NET Core 2.2 Web Api sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
    // Add a health check for a SQL database
    .AddCheck("MyDatabase", new SqlConnectionHealthCheck(Configuration["ConnectionStrings:DefaultConnection"]));
}
```

<span data-ttu-id="08843-125">Önceki kodda `services.AddHealthChecks()` yöntemi, "sağlıklı" ile **200** durum kodunu döndüren temel bir http denetimini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="08843-125">In the previous code, the `services.AddHealthChecks()` method configures a basic HTTP check that returns a status code **200** with “Healthy”.</span></span>  <span data-ttu-id="08843-126">Ayrıca, `AddCheck()` uzantısı yöntemi, ilgili SQL veritabanının sistem durumunu denetleyen özel bir `SqlConnectionHealthCheck` yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="08843-126">Further, the `AddCheck()` extension method configures a custom `SqlConnectionHealthCheck` that checks the related SQL Database’s health.</span></span>

<span data-ttu-id="08843-127">`AddCheck()` yöntemi, belirtilen bir ad ve `IHealthCheck`türünde uygulamayla yeni bir sistem durumu denetimi ekler.</span><span class="sxs-lookup"><span data-stu-id="08843-127">The `AddCheck()` method adds a new health check with a specified name and the implementation of type `IHealthCheck`.</span></span> <span data-ttu-id="08843-128">AddCheck metodunu kullanarak birden çok sistem durumu denetimi ekleyebilirsiniz, bu nedenle bir mikro hizmet, tüm denetimleri sağlıklı olana kadar "sağlıklı" bir durum sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="08843-128">You can add multiple Health Checks using AddCheck method, so a microservice won't provide a “healthy” status until all its checks are healthy.</span></span>

<span data-ttu-id="08843-129">`SqlConnectionHealthCheck`, bir bağlantı dizesini Oluşturucu parametresi olarak alan ve SQL veritabanı bağlantısının başarılı olup olmadığını kontrol etmek için basit bir sorgu yürüten `IHealthCheck`uygulayan özel bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="08843-129">`SqlConnectionHealthCheck` is a custom class that implements `IHealthCheck`, which takes a connection string as a constructor parameter and executes a simple query to check if the connection to the SQL database is successful.</span></span> <span data-ttu-id="08843-130">Sorgu başarıyla yürütülürse ve başarısız olduğunda gerçek özel duruma sahip bir `FailureStatus` `HealthCheckResult.Healthy()` döndürür.</span><span class="sxs-lookup"><span data-stu-id="08843-130">It returns `HealthCheckResult.Healthy()` if the query was executed successfully and a `FailureStatus` with the actual exception when it fails.</span></span>

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

<span data-ttu-id="08843-131">Önceki kodda `Select 1` veritabanının durumunu denetlemek için kullanılan sorgu olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="08843-131">Note that in the previous code, `Select 1` is the query used to check the Health of the database.</span></span> <span data-ttu-id="08843-132">Mikro hizmetlerinizin kullanılabilirliğini izlemek için, Kubernetes gibi düzenleyiciler ve Service Fabric mikro hizmetleri test etmek üzere istek göndererek düzenli aralıklarla durum denetimleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="08843-132">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="08843-133">Bu işlemlerin hızlı olması için veritabanı sorgularınızın etkili tutulması ve kaynakların daha yüksek kullanımına neden olması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="08843-133">It's important to keep your database queries efficient so that these operations are quick and don’t result in a higher utilization of resources.</span></span>

<span data-ttu-id="08843-134">Son olarak, "/HC" URL yoluna yanıt veren bir ara yazılım oluşturun:</span><span class="sxs-lookup"><span data-stu-id="08843-134">Finally, create a middleware that responds to the url path “/hc”:</span></span>

```csharp
// Startup.cs from .NET Core 2.2 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecks("/hc");
    //…
}
```

<span data-ttu-id="08843-135">Uç nokta `<yourmicroservice>/hc` çağrıldığında, başlangıç sınıfındaki `AddHealthChecks()` yönteminde yapılandırılan tüm sistem durumu denetimlerini çalıştırır ve sonucu gösterir.</span><span class="sxs-lookup"><span data-stu-id="08843-135">When the endpoint `<yourmicroservice>/hc` is invoked, it runs all the health checks that are configured in the `AddHealthChecks()` method in the Startup class and shows the result.</span></span>

### <a name="healthchecks-implementation-in-eshoponcontainers"></a><span data-ttu-id="08843-136">EShopOnContainers 'da Healthdenetimlerin uygulanması</span><span class="sxs-lookup"><span data-stu-id="08843-136">HealthChecks implementation in eShopOnContainers</span></span>

<span data-ttu-id="08843-137">EShopOnContainers 'daki mikro hizmetler, görevini gerçekleştirmek için birden çok hizmete bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="08843-137">Microservices in eShopOnContainers rely on multiple services to perform its task.</span></span> <span data-ttu-id="08843-138">Örneğin, eShopOnContainers 'dan `Catalog.API` mikro hizmeti, Azure Blob depolama, SQL Server ve Kbbitmq gibi birçok hizmete bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="08843-138">For example, the `Catalog.API` microservice from eShopOnContainers depends on many services, such as Azure Blob Storage, SQL Server, and RabbitMQ.</span></span> <span data-ttu-id="08843-139">Bu nedenle, `AddCheck()` yöntemi kullanılarak birçok sistem durumu denetimi eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="08843-139">Therefore, it has several health checks added using the `AddCheck()` method.</span></span> <span data-ttu-id="08843-140">Her bağımlı hizmet için, ilgili sistem durumunu tanımlayan özel bir `IHealthCheck` uygulamasının eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="08843-140">For every dependent service, a custom `IHealthCheck` implementation that defines its respective health status needs to be added.</span></span>

<span data-ttu-id="08843-141">Açık kaynaklı proje [Aspnetcore. Diagnostics. healthcheck](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) , .net Core 2,2 üzerinde oluşturulan bu kurumsal hizmetlerden her biri için özel sistem durumu denetimi uygulamaları sağlayarak bu sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="08843-141">The open-source project [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) solves this problem by providing custom health check implementations for each of these enterprise services that are built on top of .NET Core 2.2.</span></span> <span data-ttu-id="08843-142">Her bir sistem durumu denetimi, projeye kolaylıkla eklenebilen tek bir NuGet paketi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="08843-142">Each health check is available as an individual NuGet package that can be easily added to the project.</span></span> <span data-ttu-id="08843-143">eShopOnContainers bunları, tüm mikro hizmetlerinde kapsamlı olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="08843-143">eShopOnContainers use them extensively in all its microservices.</span></span>

<span data-ttu-id="08843-144">Örneğin, `Catalog.API` mikro hizmetinde aşağıdaki NuGet paketleri eklendi:</span><span class="sxs-lookup"><span data-stu-id="08843-144">For instance, in the `Catalog.API` microservice, the following NuGet packages were added:</span></span>

![AspNetCore. Diagnostics. Healthbir ekran görüntüsü NuGet paketlerini denetler.](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

<span data-ttu-id="08843-146">**Şekil 8-7**.</span><span class="sxs-lookup"><span data-stu-id="08843-146">**Figure 8-7**.</span></span> <span data-ttu-id="08843-147">AspNetCore. Diagnostics. Healthdenetimleri kullanılarak Catalog. API dosyasında uygulanan özel durum denetimleri</span><span class="sxs-lookup"><span data-stu-id="08843-147">Custom Health Checks implemented in Catalog.API using AspNetCore.Diagnostics.HealthChecks</span></span>

<span data-ttu-id="08843-148">Aşağıdaki kodda, her bağımlı hizmet için sistem durumu denetimi uygulamaları eklenir ve ardından ara yazılım yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="08843-148">In the following code, the health check implementations are added for each dependent service and then the middleware is configured:</span></span>

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

<span data-ttu-id="08843-149">Son olarak, "/HC" uç noktasını dinlemek için HealthCheck ara yazılımını ekliyoruz:</span><span class="sxs-lookup"><span data-stu-id="08843-149">Finally, we add the HealthCheck middleware to listen to “/hc” endpoint:</span></span>

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="08843-150">Mikro hizmetlerinizi, sistem durumu hakkında raporlamak için sorgulayın</span><span class="sxs-lookup"><span data-stu-id="08843-150">Query your microservices to report about their health status</span></span>

<span data-ttu-id="08843-151">Bu makalede açıklandığı şekilde sistem durumu denetimleri yapılandırdığınızda ve mikro hizmeti Docker 'da çalışıyorsa, iyi durumda bir tarayıcıdan doğrudan kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08843-151">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span> <span data-ttu-id="08843-152">Kapsayıcı bağlantı noktasını Docker konağında yayımlamanız gerekir. bu sayede, Şekil 8-8 ' de gösterildiği gibi, kapsayıcıya dış Docker ana bilgisayar IP 'si veya `localhost`aracılığıyla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08843-152">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![Bir sistem durumu denetimi tarafından döndürülen JSON yanıtının ekran görüntüsü.](./media/monitor-app-health/health-check-json-response.png)

<span data-ttu-id="08843-154">**Şekil 8-8**.</span><span class="sxs-lookup"><span data-stu-id="08843-154">**Figure 8-8**.</span></span> <span data-ttu-id="08843-155">Bir tarayıcıdan tek bir hizmetin sistem durumunu denetleme</span><span class="sxs-lookup"><span data-stu-id="08843-155">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="08843-156">Bu testte, `Catalog.API` mikro hizmetinin (5101 bağlantı noktasında çalışan) sağlıklı olduğunu, HTTP durum 200 ve durum bilgilerini JSON 'da döndürdüğünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08843-156">In that test, you can see that the `Catalog.API` microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="08843-157">Hizmet Ayrıca, SQL Server veritabanı bağımlılığının ve Kbbitmq 'in sistem durumunu kontrol etti, bu nedenle sistem durumu denetimi kendisini sağlıklı olarak raporladı.</span><span class="sxs-lookup"><span data-stu-id="08843-157">The service also checked the health of its SQL Server database dependency and RabbitMQ, so the health check reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="08843-158">Watchdogs kullanma</span><span class="sxs-lookup"><span data-stu-id="08843-158">Use watchdogs</span></span>

<span data-ttu-id="08843-159">İzleme, hizmetler genelinde sistem durumunu izleyebilecek ve daha önce tanıtılan `HealthChecks` kitaplığıyla sorgulama yaparak mikro hizmetlerle ilgili sistem durumunu rapor eden ayrı bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="08843-159">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="08843-160">Bu, tek bir hizmetin görünümüne göre algılanamayan hataları önlemeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="08843-160">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="08843-161">Watchdogs Ayrıca, Kullanıcı etkileşimi olmadan bilinen koşullar için düzeltme eylemleri gerçekleştirebilen kodu barındırmak için iyi bir yerdir.</span><span class="sxs-lookup"><span data-stu-id="08843-161">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="08843-162">EShopOnContainers örneği, Şekil 8-9 ' de gösterildiği gibi, örnek sistem durumu denetimi raporlarını görüntüleyen bir Web sayfası içerir.</span><span class="sxs-lookup"><span data-stu-id="08843-162">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="08843-163">Bu, yalnızca mikro hizmetlerin ve eShopOnContainers 'daki Web uygulamalarının durumunu gösterdiği için, sahip olduğunuz en basit izleme budur.</span><span class="sxs-lookup"><span data-stu-id="08843-163">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="08843-164">Genellikle bir izleme uygun olmayan durumları algıladığında de Eylemler gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="08843-164">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

<span data-ttu-id="08843-165">Neyse ki, [aspnetcore. Diagnostics. healthcheck](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) Ayrıca, yapılandırılmış URI 'lerden gelen sistem durumu denetimi sonuçlarını göstermek Için kullanılabilen [Aspnetcore. HEALTHCHECK. UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet paketini de sağlar.</span><span class="sxs-lookup"><span data-stu-id="08843-165">Fortunately, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) also provides [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet package that can be used to display the health check results from the configured URIs.</span></span>

![Sistem durumu denetimleri kullanıcı arabirimi eShopOnContainers durum durumlarının ekran görüntüsü.](./media/monitor-app-health/health-check-status-ui.png)

<span data-ttu-id="08843-167">**Şekil 8-9**.</span><span class="sxs-lookup"><span data-stu-id="08843-167">**Figure 8-9**.</span></span> <span data-ttu-id="08843-168">EShopOnContainers 'daki örnek durum denetimi raporu</span><span class="sxs-lookup"><span data-stu-id="08843-168">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="08843-169">Özet olarak, bu izleme hizmeti her mikro hizmetin "/HC" uç noktasını sorgular.</span><span class="sxs-lookup"><span data-stu-id="08843-169">In summary, this watchdog service queries each microservice’s "/hc" endpoint.</span></span> <span data-ttu-id="08843-170">Bu, içinde tanımlanan tüm sistem durumu denetimlerini yürütür ve tüm bu denetimlerine bağlı olarak genel bir sistem durumu döndürür.</span><span class="sxs-lookup"><span data-stu-id="08843-170">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span> <span data-ttu-id="08843-171">Healthchecksuı, birkaç yapılandırma girişi ve izleme hizmetinin Startup.cs eklenmesi gereken iki satırlık kod ile kolayca tüketicektir.</span><span class="sxs-lookup"><span data-stu-id="08843-171">The HealthChecksUI is easy to consume with a few configuration entries and two lines of code that needs to be added into the Startup.cs of the watchdog service.</span></span>

<span data-ttu-id="08843-172">Sistem durumu denetimi kullanıcı arabirimi için örnek yapılandırma dosyası:</span><span class="sxs-lookup"><span data-stu-id="08843-172">Sample configuration file for health check UI:</span></span>

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

<span data-ttu-id="08843-173">Healthchecksuı ekleyen Startup.cs dosyası:</span><span class="sxs-lookup"><span data-stu-id="08843-173">Startup.cs file that adds HealthChecksUI:</span></span>

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

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="08843-174">Düzenleyiciler kullanılırken durum denetimleri</span><span class="sxs-lookup"><span data-stu-id="08843-174">Health checks when using orchestrators</span></span>

<span data-ttu-id="08843-175">Mikro hizmetlerinizin kullanılabilirliğini izlemek için, Kubernetes gibi düzenleyiciler ve Service Fabric mikro hizmetleri test etmek üzere istek göndererek düzenli aralıklarla durum denetimleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="08843-175">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="08843-176">Bir Orchestrator bir hizmetin/kapsayıcının sağlıksız olduğunu belirlediğinde, bu örneğe yönlendirme isteklerini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="08843-176">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="08843-177">Ayrıca genellikle bu kapsayıcının yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="08843-177">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="08843-178">Örneğin, çoğu düzenleyen, sıfır kesinti dağıtımlarını yönetmek için sistem durumu denetimlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="08843-178">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="08843-179">Yalnızca bir hizmet/kapsayıcının durumu sağlıklı olarak değiştiğinde, Orchestrator başlatması trafiği hizmet/kapsayıcı örneklerine yönlendirmektedir.</span><span class="sxs-lookup"><span data-stu-id="08843-179">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="08843-180">Bir Orchestrator uygulama yükseltmesi gerçekleştirdiğinde sistem durumu izleme özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="08843-180">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="08843-181">Bazı düzenleyiciler (Azure Service Fabric) aşamalarda güncelleştirme hizmetleri — Örneğin, her uygulama yükseltmesi için küme yüzeyinin bir beşinci birini güncelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="08843-181">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="08843-182">Aynı anda yükseltilen düğüm kümesi, *yükseltme etki alanı*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="08843-182">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="08843-183">Her yükseltme etki alanı yükseltildikten ve kullanıcılar tarafından kullanılabilir olduktan sonra, dağıtım bir sonraki yükseltme etki alanına geçmeden önce bu yükseltme etki alanı, sistem durumu denetimleri iletmelidir.</span><span class="sxs-lookup"><span data-stu-id="08843-183">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="08843-184">Hizmet sistem durumunun başka bir yönü, hizmetten rapor ölçümleridir.</span><span class="sxs-lookup"><span data-stu-id="08843-184">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="08843-185">Bu, Service Fabric gibi bazı düzenleyicilerinin durum modelinin gelişmiş bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="08843-185">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="08843-186">Kaynak kullanımını dengelemek için kullanıldıklarından, bir Orchestrator kullanılırken ölçümler önemlidir.</span><span class="sxs-lookup"><span data-stu-id="08843-186">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="08843-187">Ölçümler Ayrıca sistem durumunun bir göstergesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="08843-187">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="08843-188">Örneğin, çok sayıda mikro hizmeti olan bir uygulamanız olabilir ve her örnek, saniye başına istek (RPS) ölçümünü rapor edebilir.</span><span class="sxs-lookup"><span data-stu-id="08843-188">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="08843-189">Bir hizmet başka bir hizmetten daha fazla kaynak (bellek, işlemci vb.) kullanıyorsa, Orchestrator kaynak kullanımını bile sürdürmek için hizmet örneklerini kümedeki etrafında taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="08843-189">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="08843-190">Azure Service Fabric 'in kendi [sistem durumu izleme modelini](/azure/service-fabric/service-fabric-health-introduction)sağladığını, bu da basit sistem durumu denetimlerinden daha gelişmiş olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="08843-190">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="08843-191">Gelişmiş izleme: görselleştirme, analiz ve uyarılar</span><span class="sxs-lookup"><span data-stu-id="08843-191">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="08843-192">İzlemenin son bölümü, olay akışını görselleştirme, hizmet performansını raporlama ve bir sorun algılandığında uyarma.</span><span class="sxs-lookup"><span data-stu-id="08843-192">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="08843-193">İzlemenin bu yönü için farklı çözümler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08843-193">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="08843-194">[Aspnetcore. Diagnostics. Healthdenetimlerini](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks)açıklayarak gösterilen özel sayfa gibi, hizmetlerinizin durumunu gösteren basit özel uygulamalar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08843-194">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span></span> <span data-ttu-id="08843-195">Ya da olayları akışa göre uyarıları yükseltmek için [Azure izleyici](https://azure.microsoft.com/services/monitor/) gibi daha gelişmiş araçlar da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08843-195">Or you could use more advanced tools like [Azure Monitor](https://azure.microsoft.com/services/monitor/) to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="08843-196">Son olarak, tüm olay akışlarını depoluyorsanız, verileri görselleştirmek için Microsoft Power BI veya kibana ya da splunk gibi diğer çözümleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08843-196">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="08843-197">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="08843-197">Additional resources</span></span>

- <span data-ttu-id="08843-198">**ASP.NET Core \ Için healthdenetimleri ve healthdenetimleri Kullanıcı arabirimi**</span><span class="sxs-lookup"><span data-stu-id="08843-198">**HealthChecks and HealthChecks UI for ASP.NET Core** \</span></span>
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- <span data-ttu-id="08843-199">**Service Fabric sistem durumu Izlemeye giriş** </span><span class="sxs-lookup"><span data-stu-id="08843-199">**Introduction to Service Fabric health monitoring** </span></span>\
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="08843-200">**Azure Izleyici**</span><span class="sxs-lookup"><span data-stu-id="08843-200">**Azure Monitor**</span></span>  
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
><span data-ttu-id="08843-201">[Önceki](implement-circuit-breaker-pattern.md)
>[İleri](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="08843-201">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>
