---
title: Sistem durumu izleme
description: Sistem durumu izleme uygulama yollarından keşfedin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 666b55608ca4e5d18448e1a0b4a1735f3e856474
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362489"
---
# <a name="health-monitoring"></a><span data-ttu-id="660c4-103">Sistem durumu izleme</span><span class="sxs-lookup"><span data-stu-id="660c4-103">Health monitoring</span></span>

<span data-ttu-id="660c4-104">Sistem durumu izleme, kapsayıcılar ve mikro hizmet durumu hakkında neredeyse gerçek zamanlı bilgi izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="660c4-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="660c4-105">Sistem durumu izleme, kritik işletme mikro hizmetler birçok yönünü ve düzenleyicileri kısmi uygulama yükseltmeleri aşamalarında, daha sonra açıklandığı gibi gerçekleştirin, özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="660c4-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="660c4-106">Mikro hizmet tabanlı uygulamalar genellikle sinyal kullanabilir veya kendi performans izleyicileri, zamanlayıcılar ve düzenleyicileri birçok izlemenize olanak sağlamak için sistem durumu denetimleri.</span><span class="sxs-lookup"><span data-stu-id="660c4-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="660c4-107">Hizmetleri "I canlı" bir sinyal çeşit isteğe bağlı veya bir zamanlamaya göre gönderemiyorsanız riskleri uygulamanızı yüz güncelleştirmelerini dağıtma veya yalnızca çok geç hatalarını algılamak ve ana kesintilerine sona erdirebilirsiniz zincirleme hatalara durdurmak mümkün olmaması.</span><span class="sxs-lookup"><span data-stu-id="660c4-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="660c4-108">Tipik modelinde Hizmetleri durumlarını hakkında raporlar gönderin ve uygulama durumunu durumunun genel bir görünümünü sağlamak için bu bilgileri toplanır.</span><span class="sxs-lookup"><span data-stu-id="660c4-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="660c4-109">Bir orchestrator kullanıyorsanız, küme uygun şekilde işlem yapabilmesi, düzenleyicinin küme sistem durumu bilgilerini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="660c4-109">If you're using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="660c4-110">Uygulamanız için özelleştirilmiş, yüksek kaliteli sistem durumu raporlama yatırım yaparsanız, algılayın ve çalışan uygulamanız için çok daha kolay sorunları giderin.</span><span class="sxs-lookup"><span data-stu-id="660c4-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="660c4-111">ASP.NET Core Hizmetleri uygulama durum denetimleri</span><span class="sxs-lookup"><span data-stu-id="660c4-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="660c4-112">Bir ASP.NET Core mikro hizmet veya web uygulama geliştirirken, Deneysel bir bant dışı kitaplığı kullanabilirsiniz (resmi olarak ASP.NETCore parçası olduğunu ve artık kullanım dışı) adlı *durum denetimleri* ASP.NET ekibinden.</span><span class="sxs-lookup"><span data-stu-id="660c4-112">When developing an ASP.NET Core microservice or web application, you can use an experimental out-of-band library (not official as part of ASP.NETCore and now deprecated) named *Health Checks* from the ASP.NET team.</span></span> <span data-ttu-id="660c4-113">Şu anda kullanılabilir [dotnet-mimari GitHub deposu](https://github.com/dotnet-architecture/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="660c4-113">It's available at this [dotnet-architecture GitHub repository](https://github.com/dotnet-architecture/HealthChecks).</span></span> <span data-ttu-id="660c4-114">Ancak, resmi sürümü *durum denetimleri* [içinde ASP.NET Core 2.2 yayımlanacak](https://github.com/aspnet/Announcements/issues/307) (resmi olarak 2018 sonuna kadar serbest bırakılması).</span><span class="sxs-lookup"><span data-stu-id="660c4-114">However, the official version of *Health Checks* [will be released in ASP.NET Core 2.2](https://github.com/aspnet/Announcements/issues/307) (Should be officially released by the end of 2018).</span></span>

<span data-ttu-id="660c4-115">Bu kitaplık kullanımı kolaydır ve uygulamanız (örneğin, bir SQL Server veritabanı veya Uzak API) için gereken tüm belirli dış kaynak düzgün şekilde çalıştığını doğrulama olanak sağlayan özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="660c4-115">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="660c4-116">Bu kitaplığı kullandığınızda, daha sonra anlatıldığı şekilde resource sağlam, anlamı da karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="660c4-116">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="660c4-117">Bu kitaplığı kullanmak için öncelikle mikro hizmetlerin kitaplıkta kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="660c4-117">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="660c4-118">İkinci olarak, sorgular bir ön uç uygulaması için sistem durumu raporlarının gerekir.</span><span class="sxs-lookup"><span data-stu-id="660c4-118">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="660c4-119">Ön uç uygulaması, bir özel raporlama uygulaması olabilir ya da uygun şekilde tepki verebilir bir orchestrator kendisini olabileceği için sağlık durumlarını.</span><span class="sxs-lookup"><span data-stu-id="660c4-119">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="660c4-120">Arka uç ASP.NET mikro hizmetlerin HealthChecks kitaplıkta kullan</span><span class="sxs-lookup"><span data-stu-id="660c4-120">Use the HealthChecks library in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="660c4-121">HealthChecks kitaplığı hizmetine örnek uygulamada nasıl kullanıldığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="660c4-121">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="660c4-122">Başlamak için her bir mikro hizmet durumu sağlıklı nelerden tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="660c4-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="660c4-123">Örnek uygulamada, mikro hizmetler, HTTP ve ilgili SQL Server veritabanını da kullanılabilir olup olmadığını API mikro hizmet erişilemez iyi durumda.</span><span class="sxs-lookup"><span data-stu-id="660c4-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="660c4-124">Gelecekte bir NuGet paketi olarak HealthChecks kitaplığını yüklemek mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="660c4-124">In the future, you'll be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="660c4-125">Ancak bu makalenin yazıldığı tarih itibarıyla, indirmek ve çözümünüzün bir parçası olarak Kodu derlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="660c4-125">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="660c4-126">Kullanılabilir kod klonlama <https://github.com/dotnet-architecture/HealthChecks> ve çözümünüze aşağıdaki klasörleri kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="660c4-126">Clone the code available at <https://github.com/dotnet-architecture/HealthChecks> and copy the following folders to your solution:</span></span>

- <span data-ttu-id="660c4-127">src/ortak</span><span class="sxs-lookup"><span data-stu-id="660c4-127">src/common</span></span>
- <span data-ttu-id="660c4-128">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="660c4-128">src/Microsoft.AspNetCore.HealthChecks</span></span>
- <span data-ttu-id="660c4-129">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="660c4-129">src/Microsoft.Extensions.HealthChecks</span></span>
- <span data-ttu-id="660c4-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="660c4-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="660c4-131">Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ancak bu sürümü hizmetine Azure'da herhangi bir bağımlılığı olmadığından olanlar gibi ek denetimler de kullanabilirsiniz, bunun gerekmez.</span><span class="sxs-lookup"><span data-stu-id="660c4-131">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="660c4-132">ASP.NET Core, hizmetine dayandığından, ASP.NET sistem durumu denetimleri ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="660c4-132">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="660c4-133">Şekil 8-7, Visual Studio, bir yapı taşı olarak herhangi bir mikro hizmetler tarafından kullanılmaya hazır HealthChecks kitaplığı gösterir.</span><span class="sxs-lookup"><span data-stu-id="660c4-133">Figure 8-7 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![Çözüm Gezgini görünümü HealthChecks klasörünün üç proje gösteriliyor.](./media/image6.png)

<span data-ttu-id="660c4-135">**Şekil 8-7**.</span><span class="sxs-lookup"><span data-stu-id="660c4-135">**Figure 8-7**.</span></span> <span data-ttu-id="660c4-136">ASP.NET Core HealthChecks kitaplığı kaynak kodunu bir Visual Studio çözümü içinde</span><span class="sxs-lookup"><span data-stu-id="660c4-136">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="660c4-137">Daha önce sunulan gibi her bir mikro hizmet projesine yapılacak ilk şey bir başvuru üç HealthChecks kitaplıkları eklemektir.</span><span class="sxs-lookup"><span data-stu-id="660c4-137">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="660c4-138">Bundan sonra bu mikro hizmet içinde gerçekleştirmek istediğiniz sistem durumu denetimi eylemlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="660c4-138">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="660c4-139">Bu eylemler temel olarak diğer mikro hizmetler (HttpUrlCheck) veya veritabanlarını bağımlılıkları olan (şu anda SqlCheck\* SQL Server veritabanları için).</span><span class="sxs-lookup"><span data-stu-id="660c4-139">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="660c4-140">Eylem içinde her ASP.NET mikro hizmet veya ASP.NET web uygulaması başlangıç sınıfı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="660c4-140">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="660c4-141">Her hizmeti veya web uygulamasına bir AddHealthCheck yöntemi olarak HTTP ya da veritabanı tüm bağımlılıkları ekleyerek yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="660c4-141">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="660c4-142">Örneğin, MVC web hizmetine uygulamadan birden çok hizmete bağlıdır, bu nedenle, sistem durumu denetimleri için eklenen çeşitli AddCheck yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="660c4-142">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="660c4-143">Örneğin, (Basitleştirilmiş) aşağıdaki kodda nasıl Kataloğu mikro hizmet kendi SQL Server veritabanı üzerinde bir bağımlılık ekler görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="660c4-143">For instance, in the following (simplified) code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

```csharp
// Startup.cs from Catalog.api microservice
//
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Add framework services
        services.AddHealthChecks(checks =>
        {
            checks.AddSqlCheck("CatalogDb", Configuration["ConnectionString"]);
        });
        // Other services
    }
}
```

<span data-ttu-id="660c4-144">Ancak, hizmetine MVC web uygulaması, mikro hizmetler geri kalanı üzerinde birden çok bağımlılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="660c4-144">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="660c4-145">Bu nedenle, bir AddUrlCheck yöntemini her mikro hizmet için (Basitleştirilmiş) aşağıdaki örnekte gösterildiği gibi çağırır:</span><span class="sxs-lookup"><span data-stu-id="660c4-145">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following (simplified) example:</span></span>

```csharp
// Startup.cs from the MVC web app
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
        services.Configure<AppSettings>(Configuration);
        services.AddHealthChecks(checks =>
        {
            checks.AddUrlCheck(Configuration["CatalogUrl"]);
            checks.AddUrlCheck(Configuration["OrderingUrl"]);
            checks.AddUrlCheck(Configuration["BasketUrl"]);
            checks.AddUrlCheck(Configuration["IdentityUrl"]);
        });
    }
}
```

<span data-ttu-id="660c4-146">Bu nedenle, tüm denetimleri de sağlıklı olduğunu kadar bir mikro hizmet "iyi" duruma sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="660c4-146">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="660c4-147">Mikro hizmet veya SQL Server bir bağımlılık yoksa, yalnızca bir Healthy("Ok") onay eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="660c4-147">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="660c4-148">Aşağıdaki kodu hizmetine olan `basket.api` mikro hizmet.</span><span class="sxs-lookup"><span data-stu-id="660c4-148">The following code is from the eShopOnContainers `basket.api` microservice.</span></span> <span data-ttu-id="660c4-149">(Redis cache sepet mikro hizmet kullanır, ancak kitaplık bir Redis sistem durumu denetimi sağlayıcısı henüz içermez.)</span><span class="sxs-lookup"><span data-stu-id="660c4-149">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="660c4-150">Etkinleştirmek olan sistem durumu onay uç noktası kullanıma sunmak bir hizmeti veya web uygulaması için `UseHealthChecks([*url_for_health_checks*])` genişletme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="660c4-150">For a service or web application to expose the health check endpoint, it has to enable the `UseHealthChecks([*url_for_health_checks*])` extension method.</span></span> <span data-ttu-id="660c4-151">Bu yöntem, gider `WebHostBuilder` ana yöntemi düzeyde `Program` ASP.NET Core hizmeti veya web uygulamanız, sonra sağ sınıfının <xref:Microsoft.AspNetCore.WebHost.CreateDefaultBuilder> Basitleştirilmiş aşağıdaki kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="660c4-151">This method goes at the `WebHostBuilder` level in the main method of the `Program` class of your ASP.NET Core service or web application, right after <xref:Microsoft.AspNetCore.WebHost.CreateDefaultBuilder> as shown in the following simplified code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = WebHost.CreateDefaultBuilder(args)
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseStartup<Startup>()
                .Build();

            host.Run();
        }
    }
}
```

<span data-ttu-id="660c4-152">İşlem bu şekilde çalışır: her mikro hizmet uç noktası HC kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="660c4-152">The process works this way: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="660c4-153">Uç noktanın HealthChecks kitaplığı ASP.NET Core ara yazılımı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="660c4-153">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="660c4-154">Uç noktanın çağrıldığında başlangıç sınıfındaki AddHealthChecks yöntemi yapılandırılan tüm sistem durumu denetimleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="660c4-154">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="660c4-155">Bir bağlantı noktası veya yol UseHealthChecks yöntemi bekliyor.</span><span class="sxs-lookup"><span data-stu-id="660c4-155">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="660c4-156">Bu bağlantı noktası veya yol, hizmetin sistem durumunu denetlemek için uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="660c4-156">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="660c4-157">Örneğin, katalog mikro hizmet yolu HC kullanır.</span><span class="sxs-lookup"><span data-stu-id="660c4-157">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="cache-health-check-responses"></a><span data-ttu-id="660c4-158">Önbellek sistem durumu onay yanıtları</span><span class="sxs-lookup"><span data-stu-id="660c4-158">Cache health check responses</span></span>

<span data-ttu-id="660c4-159">Çok sık hizmetlerinizde bir hizmet reddi (DoS) neden istemediğiniz veya yalnızca kaynak kontrol ederek hizmet performansı etkileyecek şekilde istemiyorsanız bu yana önbelleğe döndürür ve önbelleğe alma süresi her sistem durumu denetimi için yapılandırma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="660c4-159">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="660c4-160">Varsayılan olarak, önbelleğe alma süresi 5 dakika ile dahili olarak ayarlanır, ancak bu önbelleğe alma süresi şu kod gibi her sistem durumu denetimi üzerinde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="660c4-160">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="660c4-161">Mikro hizmetlerin sistem durumlarına raporlamak sorgulama</span><span class="sxs-lookup"><span data-stu-id="660c4-161">Query your microservices to report about their health status</span></span>

<span data-ttu-id="660c4-162">Sağlıksız olması durumunda bu makalede anlatıldığı gibi sistem durumu denetimleri yapılandırdıysanız ve Docker'da çalışan mikro hizmet sahip olduğunda, doğrudan bir tarayıcıdan denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="660c4-162">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span>

<span data-ttu-id="660c4-163">Kapsayıcı dış Docker ana bilgisayar IP üzerinden veya aracılığıyla erişebilmesi için kapsayıcı bağlantı noktasından Docker konağı yayımlamak sahip olduğunuz `localhost`Şekil 8-8 ' gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="660c4-163">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![Sistem durumu denetimi tarafından döndürülen JSON yanıtı tarayıcı görünümü](./media/image7.png)

<span data-ttu-id="660c4-165">**Şekil 8-8**.</span><span class="sxs-lookup"><span data-stu-id="660c4-165">**Figure 8-8**.</span></span> <span data-ttu-id="660c4-166">Tek bir hizmet tarayıcısından sistem durumunu denetleme</span><span class="sxs-lookup"><span data-stu-id="660c4-166">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="660c4-167">Bu test, (5101 bağlantı noktasında çalışan) catalog.api mikro hizmet sağlıklı, 200 HTTP durum ve durum bilgileri JSON biçiminde döndüren görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="660c4-167">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="660c4-168">Ayrıca dahili olarak hizmet aynı zamanda SQL Server veritabanı bağımlılık durumunu iade etmeniz ve sistem durumu denetimi kendisini sağlıklı olarak rapor edilmiştir, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="660c4-168">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="660c4-169">Watchdogs kullanın</span><span class="sxs-lookup"><span data-stu-id="660c4-169">Use watchdogs</span></span>

<span data-ttu-id="660c4-170">Bir izleme sistem durumu izleme ve yük Hizmetleri ve mikro hizmetler hakkında rapor sistem durumu ile sorgulayarak ayrı bir hizmet olan `HealthChecks` kitaplığı sunulan daha önce.</span><span class="sxs-lookup"><span data-stu-id="660c4-170">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="660c4-171">Bu işlem, tek bir hizmette bir görünümü temel alarak değil algılanır hataları önlemeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="660c4-171">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="660c4-172">Watchdogs de iyi bir kullanıcı etkileşimi olmadan bilinen koşulları için düzeltme eylemleri gerçekleştirebilen konak koda yerdir.</span><span class="sxs-lookup"><span data-stu-id="660c4-172">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="660c4-173">Şekil 8-9'da gösterildiği örnek sistem durumu denetimi raporları görüntüleyen bir web sayfası hizmetine örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="660c4-173">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="660c4-174">Mikro hizmetler ve web uygulamalarının durumu hizmetine yalnızca gösterdiğinden, olabilir basit izleme budur.</span><span class="sxs-lookup"><span data-stu-id="660c4-174">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="660c4-175">Genellikle, iyi durumda olmayan durumlar algıladığında bir bekçi ayrıca eylemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="660c4-175">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![Sistem durumu hizmetine gelen beş mikro hizmetler, gösteren WebStatus uygulamasının tarayıcı görünümü](./media/image8.png)

<span data-ttu-id="660c4-177">**Şekil 8-9**.</span><span class="sxs-lookup"><span data-stu-id="660c4-177">**Figure 8-9**.</span></span> <span data-ttu-id="660c4-178">Hizmetine örnek sistem durumu denetimi raporu</span><span class="sxs-lookup"><span data-stu-id="660c4-178">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="660c4-179">Özet olarak, ASP.NET, ASP.NET Core HealthChecks kitaplığının tek sistem durumu onay uç noktası için her bir mikro hizmetin ihtiyacımızı karşılıyor.</span><span class="sxs-lookup"><span data-stu-id="660c4-179">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="660c4-180">İçinde tanımlanan tüm sistem durumu denetimleri yürütmek ve genel sistem durumuna bağlı tüm denetimleri olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="660c4-180">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="660c4-181">Gelecekteki dış kaynaklara yeni sistem durumu denetimleri Genişletilebilir HealthChecks kitaplığıdır.</span><span class="sxs-lookup"><span data-stu-id="660c4-181">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="660c4-182">Örneğin, gelecekte kitaplığı diğer veritabanları ve Redis önbelleği için sistem durumu denetimleri olacağını umuyoruz.</span><span class="sxs-lookup"><span data-stu-id="660c4-182">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="660c4-183">Birden çok hizmet veya uygulama bağımlılıkları raporlama sistem durumu kitaplığı sağlar ve sonra bu sistem durumu denetimleri üzerinde temel eylemleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="660c4-183">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="660c4-184">Düzenleyiciler kullanırken sistem durumu denetimleri</span><span class="sxs-lookup"><span data-stu-id="660c4-184">Health checks when using orchestrators</span></span>

<span data-ttu-id="660c4-185">Mikro hizmetlerin kullanılabilirliğini izlemek için Kubernetes ve Service Fabric gibi düzenleyicileri düzenli aralıklarla sistem durumu denetimleri mikro Hizmetleri test etmek için istekleri göndererek gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="660c4-185">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="660c4-186">Ne zaman bir orchestrator hizmet/kapsayıcı yönlendirme istekleri bu örneği durdurur, sağlıksız olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="660c4-186">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="660c4-187">Ayrıca genellikle, bu kapsayıcı yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="660c4-187">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="660c4-188">Örneğin, çoğu düzenleyicileri, sistem durumu denetimleri kesintisiz dağıtımlarını yönetmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="660c4-188">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="660c4-189">Yalnızca sağlıklı bir hizmeti/kapsayıcı değişiklikleri durumunu olacak orchestrator başlattığınızda hizmet/kapsayıcı örneklerine trafiği yönlendirme.</span><span class="sxs-lookup"><span data-stu-id="660c4-189">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="660c4-190">Bir orchestrator uygulama yükseltme yaparken, sistem durumu izleme özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="660c4-190">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="660c4-191">Bazı düzenleyiciler (örneğin, Azure Service Fabric) Hizmetleri'nde aşamaları güncelleştirme — Örneğin, her uygulama yükseltmesi için küme yüzeyinde bir beşinci güncelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="660c4-191">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="660c4-192">Aynı anda yükseltilir düğümleri kümesini şeklinde adlandırılan bir *yükseltme etki alanı*.</span><span class="sxs-lookup"><span data-stu-id="660c4-192">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="660c4-193">Her bir yükseltme etki alanı yükseltildi ve kullanıcılar tarafından kullanılabilir sonra dağıtım için bir sonraki yükseltme etki alanına taşınmadan önce yükseltme etki alanı sistem durumu denetimleri geçmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="660c4-193">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="660c4-194">Bir diğer unsuru hizmet sistem durumu hizmetinden alınan ölçümleri bildiriyor.</span><span class="sxs-lookup"><span data-stu-id="660c4-194">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="660c4-195">Bu, Service Fabric gibi bazı düzenleyiciler sistem durumu modeli, Gelişmiş bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="660c4-195">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="660c4-196">Ölçümler, kaynak kullanımı dengelemek için kullanıldığından bir orchestrator kullanırken önemlidir.</span><span class="sxs-lookup"><span data-stu-id="660c4-196">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="660c4-197">Ölçümleri de sistem durumu göstergesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="660c4-197">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="660c4-198">Örneğin, birçok mikro olan bir uygulama olabilir ve her örneği bir saniyede istekleri (RP'ler) ölçüm bildirir.</span><span class="sxs-lookup"><span data-stu-id="660c4-198">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="660c4-199">Bir hizmetin başka bir hizmete daha fazla kaynak (bellek, işlemci, vb.) kullanıyorsanız, orchestrator hizmet örnekleri bile kaynak kullanımını korumak için kümedeki yerleri.</span><span class="sxs-lookup"><span data-stu-id="660c4-199">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="660c4-200">Azure Service Fabric kendi sağladığını unutmayın [sistem durumu izleme modeli](/azure/service-fabric/service-fabric-health-introduction), basit bir sistem durumu denetimleri daha gelişmiş olduğu.</span><span class="sxs-lookup"><span data-stu-id="660c4-200">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="660c4-201">Gelişmiş izleme: Görselleştirme ve çözümleme uyarıları</span><span class="sxs-lookup"><span data-stu-id="660c4-201">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="660c4-202">İzleme son bölümü göre servis performansını raporlama ve bir sorun algılandığında uyarı olay akışını görselleştirme olduğu.</span><span class="sxs-lookup"><span data-stu-id="660c4-202">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="660c4-203">Bu izleme açısını için farklı çözümler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="660c4-203">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="660c4-204">Açıklayan gösterilen özel sayfa gibi hizmetlerinizin durumunu gösteren basit bir özel uygulamalar kullanabilir [ASP.NET Core HealthChecks](https://github.com/dotnet-architecture/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="660c4-204">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [ASP.NET Core HealthChecks](https://github.com/dotnet-architecture/HealthChecks).</span></span> <span data-ttu-id="660c4-205">Ya da olayların akışa göre uyarıları artırmak için Azure Application Insights gibi daha gelişmiş araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="660c4-205">Or you could use more advanced tools like Azure Application Insights to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="660c4-206">Tüm olay akışlarını depoladığınız, son olarak, Microsoft Power BI veya Kibana veya Splunk gibi diğer çözümlerle verileri görselleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="660c4-206">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="660c4-207">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="660c4-207">Additional resources</span></span>

- <span data-ttu-id="660c4-208">**ASP.NET Core HealthChecks** (Deneysel sürüm) \\</span><span class="sxs-lookup"><span data-stu-id="660c4-208">**ASP.NET Core HealthChecks** (experimental release)\\</span></span>
  [*https://github.com/dotnet-architecture/HealthChecks/*](https://github.com/dotnet-architecture/HealthChecks/)

- <span data-ttu-id="660c4-209">**Service Fabric sistem durumu izlemeye giriş**\\</span><span class="sxs-lookup"><span data-stu-id="660c4-209">**Introduction to Service Fabric health monitoring**\\</span></span>
  [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="660c4-210">**Azure Application Insights**\\</span><span class="sxs-lookup"><span data-stu-id="660c4-210">**Azure Application Insights**\\</span></span>
  [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

- <span data-ttu-id="660c4-211">**Microsoft Operations Management Suite'e**\\</span><span class="sxs-lookup"><span data-stu-id="660c4-211">**Microsoft Operations Management Suite**\\</span></span>
  [*https://www.microsoft.com/cloud-platform/operations-management-suite*](https://www.microsoft.com/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
><span data-ttu-id="660c4-212">[Önceki](implement-circuit-breaker-pattern.md)
>[İleri](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="660c4-212">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>