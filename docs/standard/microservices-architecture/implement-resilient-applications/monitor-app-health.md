---
title: Sistem durumu izleme
description: Sistem durumu izleme uygulama yollarından keşfedin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: deebcf6771d24be34050dd7fdfb807a681ebce1f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61818631"
---
# <a name="health-monitoring"></a><span data-ttu-id="2aaf1-103">Sistem durumu izleme</span><span class="sxs-lookup"><span data-stu-id="2aaf1-103">Health monitoring</span></span>

<span data-ttu-id="2aaf1-104">Sistem durumu izleme, kapsayıcılar ve mikro hizmet durumu hakkında neredeyse gerçek zamanlı bilgi izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="2aaf1-105">Sistem durumu izleme, kritik işletme mikro hizmetler birçok yönünü ve düzenleyicileri kısmi uygulama yükseltmeleri aşamalarında, daha sonra açıklandığı gibi gerçekleştirin, özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="2aaf1-106">Mikro hizmet tabanlı uygulamalar genellikle sinyal kullanabilir veya kendi performans izleyicileri, zamanlayıcılar ve düzenleyicileri birçok izlemenize olanak sağlamak için sistem durumu denetimleri.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="2aaf1-107">Hizmetleri "I canlı" bir sinyal çeşit isteğe bağlı veya bir zamanlamaya göre gönderemiyorsanız riskleri uygulamanızı yüz güncelleştirmelerini dağıtma veya yalnızca çok geç hatalarını algılamak ve ana kesintilerine sona erdirebilirsiniz zincirleme hatalara durdurmak mümkün olmaması.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="2aaf1-108">Tipik modelinde Hizmetleri durumlarını hakkında raporlar gönderin ve uygulama durumunu durumunun genel bir görünümünü sağlamak için bu bilgileri toplanır.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="2aaf1-109">Bir orchestrator kullanıyorsanız, küme uygun şekilde işlem yapabilmesi, düzenleyicinin küme sistem durumu bilgilerini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-109">If you're using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="2aaf1-110">Uygulamanız için özelleştirilmiş, yüksek kaliteli sistem durumu raporlama yatırım yaparsanız, algılayın ve çalışan uygulamanız için çok daha kolay sorunları giderin.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="2aaf1-111">ASP.NET Core Hizmetleri uygulama durum denetimleri</span><span class="sxs-lookup"><span data-stu-id="2aaf1-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="2aaf1-112">Bir ASP.NET Core mikro hizmet veya web uygulama geliştirirken, ASP .NET Core 2.2 içinde sunulan yerleşik sistem durumu denetimleri özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-112">When developing an ASP.NET Core microservice or web application, you can use the built-in health checks feature that was released in ASP .NET Core 2.2.</span></span> <span data-ttu-id="2aaf1-113">Çoğu gibi ASP.NET Core özellikleri, sistem durumu denetimleri bir dizi hizmet ve bir ara yazılım birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-113">Like many ASP.NET Core features, health checks come with a set of services and a middleware.</span></span>

<span data-ttu-id="2aaf1-114">Sistem durumu denetimi Hizmetleri ve ara yazılım kullanın ve uygulamanız (örneğin, bir SQL Server veritabanı veya bir uzak API'ye) için gerekli olan herhangi bir dış kaynağa düzgün çalıştığını doğrulamak olanak veren özellikler sağlamak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-114">Health check services and middleware are easy to use and provide capabilities that let you validate if any external resource needed for your application (like a SQL Server database or a remote API) is working properly.</span></span> <span data-ttu-id="2aaf1-115">Bu özelliği kullandığınızda, daha sonra anlatıldığı şekilde resource sağlam, anlamı da karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-115">When you use this feature, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="2aaf1-116">Bu özelliği etkili bir şekilde kullanmak için önce mikro Hizmetleri services'ı yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-116">To use this feature effectively, you need to first configure services in your microservices.</span></span> <span data-ttu-id="2aaf1-117">İkinci olarak, sorgular bir ön uç uygulaması için sistem durumu raporlarının gerekir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="2aaf1-118">Ön uç uygulaması, bir özel raporlama uygulaması olabilir ya da uygun şekilde tepki verebilir bir orchestrator kendisini olabileceği için sağlık durumlarını.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-118">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="2aaf1-119">Arka uç ASP.NET mikro hizmetlerin de HealthChecks özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="2aaf1-119">Use the HealthChecks feature in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="2aaf1-120">Bu bölümde, örnek ASP.NET Core 2.2 Web API uygulamasında HealthChecks özelliği nasıl kullanıldığını öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-120">In this section, you will learn how the HealthChecks feature is used in a sample ASP.NET Core 2.2 Web API application.</span></span> <span data-ttu-id="2aaf1-121">Bu özelliği hizmetine gibi büyük ölçekli mikro Hizmetler uygulaması sonraki bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-121">Implementation of this feature in a large scale microservices like the eShopOnContainers is explained in the later section.</span></span> <span data-ttu-id="2aaf1-122">Başlamak için her bir mikro hizmet durumu sağlıklı nelerden tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="2aaf1-123">Örnek uygulamada, mikro hizmet API'si, HTTP üzerinden erişilebilir ve ilgili SQL Server veritabanını da kullanılabilir, mikro hizmetler iyi durumda.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and its related SQL Server database is also available.</span></span>

<span data-ttu-id="2aaf1-124">Yerleşik API'leri ile .NET Core 2.2 Hizmetleri, yapılandırabileceğiniz ekleme mikro hizmet ve bu şekilde bağımlı SQL Server veritabanı için sistem durumunu denetleyin:</span><span class="sxs-lookup"><span data-stu-id="2aaf1-124">In .NET Core 2.2, with the built-in APIs, you can configure the services, add a Health Check for the microservice and its dependent SQL Server database in this way:</span></span>

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

<span data-ttu-id="2aaf1-125">Önceki kodda, `services.AddHealthChecks()` yöntemi yapılandırır bir durum kodu döndüren temel bir HTTP denetimini **200** "Sağlıklı" ile.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-125">In the previous code, the `services.AddHealthChecks()` method configures a basic HTTP check that returns a status code **200** with “Healthy”.</span></span>  <span data-ttu-id="2aaf1-126">Ayrıca `AddCheck()` özel bir genişletme yöntemi yapılandırır `SqlConnectionHealthCheck` ilgili SQL veritabanının durumu denetler.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-126">Further, the `AddCheck()` extension method configures a custom `SqlConnectionHealthCheck` that checks the related SQL Database’s health.</span></span>

<span data-ttu-id="2aaf1-127">`AddCheck()` Yöntemi, belirtilen ada ve uygulama türü ile yeni bir sistem durumu denetimi ekler `IHealthCheck`.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-127">The `AddCheck()` method adds a new health check with a specified name and the implementation of type `IHealthCheck`.</span></span> <span data-ttu-id="2aaf1-128">Birden çok durum denetimleri kadar tüm denetimleri sağlıklı bir mikro hizmet "iyi" duruma sağlamayacak şekilde AddCheck yöntemi kullanarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-128">You can add multiple Health Checks using AddCheck method, so a microservice won't provide a “healthy” status until all its checks are healthy.</span></span>

<span data-ttu-id="2aaf1-129">`SqlConnectionHealthCheck` uygulayan özel bir sınıf `IHealthCheck`, oluşturucu parametresi olarak bir bağlantı dizesi alır ve SQL veritabanı bağlantısı başarılı olup olmadığını denetlemek için basit bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-129">`SqlConnectionHealthCheck` is a custom class that implements `IHealthCheck`, which takes a connection string as a constructor parameter and executes a simple query to check if the connection to the SQL database is successful.</span></span> <span data-ttu-id="2aaf1-130">Döndürür `HealthCheckResult.Healthy()` sorgu başarıyla yürütüldü ve bir `FailureStatus` gerçek özel durumuyla başarısız olduğunda.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-130">It returns `HealthCheckResult.Healthy()` if the query was executed successfully and a `FailureStatus` with the actual exception when it fails.</span></span>

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

<span data-ttu-id="2aaf1-131">Önceki kodda, dikkat `Select 1` veritabanı durumunu kontrol etmek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-131">Note that in the previous code, `Select 1` is the query used to check the Health of the database.</span></span> <span data-ttu-id="2aaf1-132">Mikro hizmetlerin kullanılabilirliğini izlemek için Kubernetes ve Service Fabric gibi düzenleyicileri düzenli aralıklarla sistem durumu denetimleri mikro Hizmetleri test etmek için istekleri göndererek gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-132">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="2aaf1-133">Böylece bu işlemler, hızlı ve daha yüksek bir kullanımı kaynakların neden olmayan veritabanı sorgularınızı verimli tutmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-133">It's important to keep your database queries efficient so that these operations are quick and don’t result in a higher utilization of resources.</span></span>

<span data-ttu-id="2aaf1-134">Son olarak, url yoluyla "HC" yanıt veren bir ara yazılım oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2aaf1-134">Finally, create a middleware that responds to the url path “/hc”:</span></span>

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

<span data-ttu-id="2aaf1-135">Uç nokta `<yourmicroservice>/hc` olan çağrılır, yapılandırılan tüm sistem durumu denetimleri çalıştırır `AddHealthChecks()` sınıfında başlatma yöntemi ve sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-135">When the endpoint `<yourmicroservice>/hc` is invoked, it runs all the health checks that are configured in the `AddHealthChecks()` method in the Startup class and shows the result.</span></span>

### <a name="healthchecks-implementation-in-eshoponcontainers"></a><span data-ttu-id="2aaf1-136">Hizmetine HealthChecks uygulama</span><span class="sxs-lookup"><span data-stu-id="2aaf1-136">HealthChecks implementation in eShopOnContainers</span></span>

<span data-ttu-id="2aaf1-137">Mikro hizmetler hizmetine görevini gerçekleştirmek için birden çok Hizmetleri'ni kullanır.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-137">Microservices in eShopOnContainers rely on multiple services to perform its task.</span></span> <span data-ttu-id="2aaf1-138">Örneğin, `Catalog.API` hizmetine gelen mikro hizmet, Azure Blob Depolama, SQL Server ve RabbitMQ gibi birçok hizmet bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-138">For example, the `Catalog.API` microservice from eShopOnContainers depends on many services, such as Azure Blob Storage, SQL Server, and RabbitMQ.</span></span> <span data-ttu-id="2aaf1-139">Bu nedenle, bazı sistem durumu denetimleri kullanılarak eklenen sahip `AddCheck()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-139">Therefore, it has several health checks added using the `AddCheck()` method.</span></span> <span data-ttu-id="2aaf1-140">Her bir bağlı hizmet için özel bir `IHealthCheck` ilgili sistem durumunu tanımlar uygulama eklenmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-140">For every dependent service, a custom `IHealthCheck` implementation that defines its respective health status needs to be added.</span></span>

<span data-ttu-id="2aaf1-141">Açık kaynaklı proje [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) üzerinde .NET Core 2.2 oluşturulan bu enterprise hizmetlerinin her biri için özel sistem durumu denetimi uygulamaları sağlayarak bu sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-141">The open-source project [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) solves this problem by providing custom health check implementations for each of these enterprise services that are built on top of .NET Core 2.2.</span></span> <span data-ttu-id="2aaf1-142">Her sistem durumu denetimi, projeye kolayca eklenebilen tek bir NuGet paketi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-142">Each health check is available as an individual NuGet package that can be easily added to the project.</span></span> <span data-ttu-id="2aaf1-143">Hizmetine bunları kapsamlı bir şekilde kendi mikro Hizmetleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-143">eShopOnContainers use them extensively in all its microservices.</span></span>

<span data-ttu-id="2aaf1-144">Örneğin, `Catalog.API` mikro hizmet, aşağıdaki NuGet paketleri eklendi:</span><span class="sxs-lookup"><span data-stu-id="2aaf1-144">For instance, in the `Catalog.API` microservice, the following NuGet packages were added:</span></span>

![Çözüm Gezgini görünümü nerede AspNetCore.Diagnostics.HealthChecks NuGet paketlerini başvurulan Catalog.API projenin](./media/image6.png)

<span data-ttu-id="2aaf1-146">**Şekil 8-7**.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-146">**Figure 8-7**.</span></span> <span data-ttu-id="2aaf1-147">Özel durum AspNetCore.Diagnostics.HealthChecks kullanarak Catalog.API içinde uygulanan denetimleri</span><span class="sxs-lookup"><span data-stu-id="2aaf1-147">Custom Health Checks implemented in Catalog.API using AspNetCore.Diagnostics.HealthChecks</span></span>

<span data-ttu-id="2aaf1-148">Aşağıdaki kodda, bağımlı her hizmet için sistem durumu denetimi uygulamaları eklenir ve ardından Ara yazılım yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="2aaf1-148">In the following code, the health check implementations are added for each dependent service and then the middleware is configured:</span></span>

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

<span data-ttu-id="2aaf1-149">Son olarak, "/ HC" uç noktası dinleyecek şekilde HealthCheck ara yazılım ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2aaf1-149">Finally, we add the HealthCheck middleware to listen to “/hc” endpoint:</span></span>

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="2aaf1-150">Mikro hizmetlerin sistem durumlarına raporlamak sorgulama</span><span class="sxs-lookup"><span data-stu-id="2aaf1-150">Query your microservices to report about their health status</span></span>

<span data-ttu-id="2aaf1-151">Sağlıksız olması durumunda bu makalede anlatıldığı gibi sistem durumu denetimleri yapılandırdıysanız ve Docker'da çalışan mikro hizmet sahip olduğunda, doğrudan bir tarayıcıdan denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-151">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span> <span data-ttu-id="2aaf1-152">Kapsayıcı dış Docker ana bilgisayar IP üzerinden veya aracılığıyla erişebilmesi için kapsayıcı bağlantı noktasından Docker konağı yayımlamak sahip olduğunuz `localhost`Şekil 8-8 ' gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-152">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![Sistem durumu denetimi tarafından döndürülen JSON yanıtı tarayıcı görünümü](./media/image7.png)

<span data-ttu-id="2aaf1-154">**Şekil 8-8**.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-154">**Figure 8-8**.</span></span> <span data-ttu-id="2aaf1-155">Tek bir hizmet tarayıcısından sistem durumunu denetleme</span><span class="sxs-lookup"><span data-stu-id="2aaf1-155">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="2aaf1-156">Bu test, gördüğünüz gibi `Catalog.API` sağlıklı, 200 HTTP durum ve durum bilgileri JSON biçiminde döndüren mikro hizmet (5101 bağlantı noktasında çalışıyor).</span><span class="sxs-lookup"><span data-stu-id="2aaf1-156">In that test, you can see that the `Catalog.API` microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="2aaf1-157">Sistem durumu denetimi kendisini sağlıklı olarak rapor için hizmet durumunu, SQL Server veritabanı bağımlılık ve RabbitMQ, ayrıca kullanıma.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-157">The service also checked the health of its SQL Server database dependency and RabbitMQ, so the health check reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="2aaf1-158">Watchdogs kullanın</span><span class="sxs-lookup"><span data-stu-id="2aaf1-158">Use watchdogs</span></span>

<span data-ttu-id="2aaf1-159">Bir izleme sistem durumu izleme ve yük Hizmetleri ve mikro hizmetler hakkında rapor sistem durumu ile sorgulayarak ayrı bir hizmet olan `HealthChecks` kitaplığı sunulan daha önce.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-159">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="2aaf1-160">Bu işlem, tek bir hizmette bir görünümü temel alarak değil algılanır hataları önlemeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-160">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="2aaf1-161">Watchdogs de iyi bir kullanıcı etkileşimi olmadan bilinen koşulları için düzeltme eylemleri gerçekleştirebilen konak koda yerdir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-161">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="2aaf1-162">Şekil 8-9'da gösterildiği örnek sistem durumu denetimi raporları görüntüleyen bir web sayfası hizmetine örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-162">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="2aaf1-163">Mikro hizmetler ve web uygulamalarının durumu hizmetine yalnızca gösterdiğinden, olabilir basit izleme budur.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-163">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="2aaf1-164">Genellikle, iyi durumda olmayan durumlar algıladığında bir bekçi ayrıca eylemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-164">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

<span data-ttu-id="2aaf1-165">Neyse ki, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) ayrıca sağlar [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) sistem durumu denetimini görüntülemek için kullanılan NuGet paketini yapılandırılmış bir URI'leri oluşur.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-165">Fortunately, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) also provides [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet package that can be used to display the health check results from the configured URIs.</span></span>

![Sistem durumu hizmetine gelen tüm mikro hizmetler, gösteren WebStatus uygulamasının tarayıcı görünümü](./media/image8.png)

<span data-ttu-id="2aaf1-167">**Şekil 8-9**.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-167">**Figure 8-9**.</span></span> <span data-ttu-id="2aaf1-168">Hizmetine örnek sistem durumu denetimi raporu</span><span class="sxs-lookup"><span data-stu-id="2aaf1-168">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="2aaf1-169">Özet olarak, her bir mikro hizmetin ait "/ HC" uç noktası bu izleme hizmetini sorgular.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-169">In summary, this watchdog service queries each microservice’s "/hc" endpoint.</span></span> <span data-ttu-id="2aaf1-170">İçinde tanımlanan tüm sistem durumu denetimleri yürütmek ve genel sistem durumuna bağlı tüm denetimleri olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-170">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span> <span data-ttu-id="2aaf1-171">HealthChecksUI birkaç yapılandırma girdileri ve iki izleme hizmeti Startup.cs eklenmesi gereken kod satırı ile kullanmak kolay bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-171">The HealthChecksUI is easy to consume with a few configuration entries and two lines of code that needs to be added into the Startup.cs of the watchdog service.</span></span>

<span data-ttu-id="2aaf1-172">Sistem durumu için örnek yapılandırma dosyası, UI kontrol edin:</span><span class="sxs-lookup"><span data-stu-id="2aaf1-172">Sample configuration file for health check UI:</span></span>

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

<span data-ttu-id="2aaf1-173">HealthChecksUI ekler Startup.cs dosyası:</span><span class="sxs-lookup"><span data-stu-id="2aaf1-173">Startup.cs file that adds HealthChecksUI:</span></span>

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

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="2aaf1-174">Düzenleyiciler kullanırken sistem durumu denetimleri</span><span class="sxs-lookup"><span data-stu-id="2aaf1-174">Health checks when using orchestrators</span></span>

<span data-ttu-id="2aaf1-175">Mikro hizmetlerin kullanılabilirliğini izlemek için Kubernetes ve Service Fabric gibi düzenleyicileri düzenli aralıklarla sistem durumu denetimleri mikro Hizmetleri test etmek için istekleri göndererek gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-175">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="2aaf1-176">Ne zaman bir orchestrator hizmet/kapsayıcı yönlendirme istekleri bu örneği durdurur, sağlıksız olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-176">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="2aaf1-177">Ayrıca genellikle, bu kapsayıcı yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-177">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="2aaf1-178">Örneğin, çoğu düzenleyicileri, sistem durumu denetimleri kesintisiz dağıtımlarını yönetmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-178">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="2aaf1-179">Yalnızca sağlıklı bir hizmeti/kapsayıcı değişiklikleri durumunu olacak orchestrator başlattığınızda hizmet/kapsayıcı örneklerine trafiği yönlendirme.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-179">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="2aaf1-180">Bir orchestrator uygulama yükseltme yaparken, sistem durumu izleme özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-180">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="2aaf1-181">Bazı düzenleyiciler (örneğin, Azure Service Fabric) Hizmetleri'nde aşamaları güncelleştirme — Örneğin, her uygulama yükseltmesi için küme yüzeyinde bir beşinci güncelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-181">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="2aaf1-182">Aynı anda yükseltilir düğümleri kümesini şeklinde adlandırılan bir *yükseltme etki alanı*.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-182">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="2aaf1-183">Her bir yükseltme etki alanı yükseltildi ve kullanıcılar tarafından kullanılabilir sonra dağıtım için bir sonraki yükseltme etki alanına taşınmadan önce yükseltme etki alanı sistem durumu denetimleri geçmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-183">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="2aaf1-184">Bir diğer unsuru hizmet sistem durumu hizmetinden alınan ölçümleri bildiriyor.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-184">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="2aaf1-185">Bu, Service Fabric gibi bazı düzenleyiciler sistem durumu modeli, Gelişmiş bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-185">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="2aaf1-186">Ölçümler, kaynak kullanımı dengelemek için kullanıldığından bir orchestrator kullanırken önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-186">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="2aaf1-187">Ölçümleri de sistem durumu göstergesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-187">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="2aaf1-188">Örneğin, birçok mikro olan bir uygulama olabilir ve her örneği bir saniyede istekleri (RP'ler) ölçüm bildirir.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-188">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="2aaf1-189">Bir hizmetin başka bir hizmete daha fazla kaynak (bellek, işlemci, vb.) kullanıyorsanız, orchestrator hizmet örnekleri bile kaynak kullanımını korumak için kümedeki yerleri.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-189">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="2aaf1-190">Azure Service Fabric kendi sağladığını unutmayın [sistem durumu izleme modeli](/azure/service-fabric/service-fabric-health-introduction), basit bir sistem durumu denetimleri daha gelişmiş olduğu.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-190">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="2aaf1-191">Gelişmiş izleme: Görselleştirme ve çözümleme uyarıları</span><span class="sxs-lookup"><span data-stu-id="2aaf1-191">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="2aaf1-192">İzleme son bölümü göre servis performansını raporlama ve bir sorun algılandığında uyarı olay akışını görselleştirme olduğu.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-192">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="2aaf1-193">Bu izleme açısını için farklı çözümler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-193">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="2aaf1-194">Açıklayan gösterilen özel sayfa gibi hizmetlerinizin durumunu gösteren basit bir özel uygulamalar kullanabilir [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="2aaf1-194">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span></span> <span data-ttu-id="2aaf1-195">Veya gibi daha gelişmiş araçları kullanabilir [Azure İzleyici](https://azure.microsoft.com/services/monitor/) olayların akışa göre uyarıları yükseltmek için.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-195">Or you could use more advanced tools like [Azure Monitor](https://azure.microsoft.com/services/monitor/) to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="2aaf1-196">Tüm olay akışlarını depoladığınız, son olarak, Microsoft Power BI veya Kibana veya Splunk gibi diğer çözümlerle verileri görselleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaf1-196">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="2aaf1-197">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="2aaf1-197">Additional resources</span></span>

- <span data-ttu-id="2aaf1-198">**HealthChecks ve ASP.NET Core HealthChecks kullanıcı Arabirimi** \\</span><span class="sxs-lookup"><span data-stu-id="2aaf1-198">**HealthChecks and HealthChecks UI for ASP.NET Core** \\</span></span>
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- <span data-ttu-id="2aaf1-199">**Service Fabric sistem durumu izlemeye giriş** \\</span><span class="sxs-lookup"><span data-stu-id="2aaf1-199">**Introduction to Service Fabric health monitoring** \\</span></span>
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="2aaf1-200">**Azure İzleyici**
  <https://azure.microsoft.com/services/monitor/></span><span class="sxs-lookup"><span data-stu-id="2aaf1-200">**Azure Monitor**
<https://azure.microsoft.com/services/monitor/></span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2aaf1-201">[Önceki](implement-circuit-breaker-pattern.md)
>[İleri](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="2aaf1-201">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>
