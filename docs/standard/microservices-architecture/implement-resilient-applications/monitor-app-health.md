---
title: Sistem durumu izleme
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Sistem durumu izleme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 62d4e9a26710a5c4b191287bf76192972f7e991b
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106547"
---
# <a name="health-monitoring"></a><span data-ttu-id="44d63-103">Sistem durumu izleme</span><span class="sxs-lookup"><span data-stu-id="44d63-103">Health monitoring</span></span>

<span data-ttu-id="44d63-104">Sistem durumu izleme durumunu kapsayıcıları ve mikro hizmetler hakkında bilgi yakın gerçek zamanlı izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44d63-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="44d63-105">Sistem durumu izleme mikro işletim birden çok yönlerini için kritik öneme sahiptir ve orchestrators kısmi uygulama yükseltmelerini aşamalarında, daha sonra açıklandığı gibi gerçekleştirdiğinizde özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="44d63-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="44d63-106">Mikro tabanlı uygulamalar genellikle sinyal kullanabilir veya kendi performans izleyicileri, zamanlayıcılar ve orchestrators birçok izlemenize olanak sağlamak için sistem durumu denetler.</span><span class="sxs-lookup"><span data-stu-id="44d63-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="44d63-107">Hizmetleri "Canlı ben" sinyal çeşit isteğe bağlı veya bir zamanlamaya göre gönderemiyor, uygulamanız güncelleştirmeleri dağıtırken veya yalnızca hatalarını çok geç algılayacak ve önemli kesilmelerini sonlandırabilirsiniz basamaklı hataları Durdur yükleyemeyebilirsiniz riskleri karşılaşıyor.</span><span class="sxs-lookup"><span data-stu-id="44d63-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might simply detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="44d63-108">Tipik modelinde Hizmetleri durumları hakkında rapor gönderme ve sistem durumu, uygulamanızın durumunu genel bir görünümünü sağlamak için bu bilgileri toplanır.</span><span class="sxs-lookup"><span data-stu-id="44d63-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="44d63-109">Bir orchestrator kullanıyorsanız, böylece küme buna uygun olarak davranıp orchestrator'ın küme, sistem durumu bilgilerini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="44d63-109">If you are using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="44d63-110">Yüksek kaliteli sistem durumu, uygulamanız için özelleştirilmiş raporlamada yatırım algılamak ve çalışan uygulamanız için daha kolay düzeltin.</span><span class="sxs-lookup"><span data-stu-id="44d63-110">If you invest in high-quality health reporting that is customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implementing-health-checks-in-aspnet-core-services"></a><span data-ttu-id="44d63-111">Sistem durumu uygulama ASP.NET Core Hizmetleri'nde denetler</span><span class="sxs-lookup"><span data-stu-id="44d63-111">Implementing health checks in ASP.NET Core services</span></span>

<span data-ttu-id="44d63-112">Bir ASP.NET Core mikro hizmet veya web uygulama geliştirirken, bir bant dışı kitaplığını kullanabilirsiniz (değil resmi ASP.NETCore bir parçası olarak) adlı `HealthChecks` ASP.NET ekibinden.</span><span class="sxs-lookup"><span data-stu-id="44d63-112">When developing an ASP.NET Core microservice or web application, you can use an out-of-band library (not official as part of ASP.NETCore) named `HealthChecks` from the ASP.NET team.</span></span> <span data-ttu-id="44d63-113">Şu anda kullanılabilir [GitHub deposuna](https://github.com/dotnet-architecture/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="44d63-113">It is available at this [GitHub repo](https://github.com/dotnet-architecture/HealthChecks).</span></span>

<span data-ttu-id="44d63-114">Bu kitaplık kullanımı kolaydır ve uygulamanız (örneğin, bir SQL Server veritabanı veya Uzak API) için gerekli herhangi belirli bir dış kaynağa düzgün çalıştığını doğrulamak olanak sağlayan özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44d63-114">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="44d63-115">Bu kitaplık kullandığınızda, daha sonra anlatıldığı şekilde kaynağın sistem durumunun iyi olduğundan anlamını da karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44d63-115">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="44d63-116">Bu kitaplığı kullanmak için önce mikro kitaplıkta kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="44d63-116">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="44d63-117">İkinci olarak, sistem durumu raporları sorgular bir ön uç uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44d63-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="44d63-118">Ön uç uygulama, özel bir raporlama uygulama olabilir ya da, uygun şekilde tepki gösterebilmesi bir orchestrator kendisini olabilir sistem sağlığı durumları.</span><span class="sxs-lookup"><span data-stu-id="44d63-118">That front end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="44d63-119">Arka ucunuz ASP.NET mikro HealthChecks kitaplıkta kullanma</span><span class="sxs-lookup"><span data-stu-id="44d63-119">Using the HealthChecks library in your back end ASP.NET microservices</span></span>

<span data-ttu-id="44d63-120">HealthChecks kitaplığı eShopOnContainers örnek uygulama nasıl kullanıldığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44d63-120">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="44d63-121">Başlamak için her mikro hizmet durumu sağlıklı nelerin oluşturduğunu tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="44d63-121">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="44d63-122">Örnek uygulama mikro API mikro HTTP ve ilgili SQL Server veritabanını da kullanılabilir olup olmadığını aracılığıyla erişilebilir olması durumunda iyi durumda.</span><span class="sxs-lookup"><span data-stu-id="44d63-122">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="44d63-123">Gelecekte, bir NuGet paketi olarak HealthChecks Kitaplığı'nı yüklemek mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="44d63-123">In the future, you will be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="44d63-124">Ancak bu makalenin yazıldığı sırada indirmek ve çözümünüzün bir parçası olarak Kodu derlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="44d63-124">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="44d63-125">Adresinde kod kopyalama https://github.com/dotnet-architecture/HealthChecks ve aşağıdaki klasörler çözümünüze kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="44d63-125">Clone the code available at https://github.com/dotnet-architecture/HealthChecks and copy the following folders to your solution:</span></span>

  - <span data-ttu-id="44d63-126">src/ortak</span><span class="sxs-lookup"><span data-stu-id="44d63-126">src/common</span></span>
  - <span data-ttu-id="44d63-127">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="44d63-127">src/Microsoft.AspNetCore.HealthChecks</span></span>
  - <span data-ttu-id="44d63-128">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="44d63-128">src/Microsoft.Extensions.HealthChecks</span></span>
  - <span data-ttu-id="44d63-129">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="44d63-129">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="44d63-130">Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ancak bu sürümü eShopOnContainers, Azure üzerinde herhangi bir bağımlılığı olmadığından olanlar gibi ek denetimler de kullanabilirsiniz, onu gerekmez.</span><span class="sxs-lookup"><span data-stu-id="44d63-130">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="44d63-131">EShopOnContainers ASP.NET Core üzerinde bağlı olduğundan, ASP.NET durumu denetimleri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="44d63-131">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="44d63-132">Şekil 10-6 HealthChecks Kitaplığı Visual Studio, bir yapı taşı olarak tüm mikro tarafından kullanılmak üzere hazır gösterir.</span><span class="sxs-lookup"><span data-stu-id="44d63-132">Figure 10-6 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![](./media/image6.png)

<span data-ttu-id="44d63-133">**Şekil 10-6**.</span><span class="sxs-lookup"><span data-stu-id="44d63-133">**Figure 10-6**.</span></span> <span data-ttu-id="44d63-134">ASP.NET Core HealthChecks kitaplığı kaynak kodundaki bir Visual Studio çözümü</span><span class="sxs-lookup"><span data-stu-id="44d63-134">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="44d63-135">Daha önce sunulan gibi her mikro hizmet projesinde yapılacak ilk şey üç HealthChecks kitaplıklar için bir başvuru eklemeniz gereklidir.</span><span class="sxs-lookup"><span data-stu-id="44d63-135">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="44d63-136">Bundan sonra o mikro gerçekleştirmek istediğiniz sistem durumu denetimi eylemlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="44d63-136">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="44d63-137">Bu eylemler temelde diğer mikro (HttpUrlCheck) veya veritabanlarını bağımlılıklardır (şu anda SqlCheck\* SQL Server veritabanları için).</span><span class="sxs-lookup"><span data-stu-id="44d63-137">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="44d63-138">Eylem içinde her ASP.NET mikro hizmet veya ASP.NET web uygulaması başlangıç sınıfı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="44d63-138">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="44d63-139">Her hizmeti veya web uygulamasını bir AddHealthCheck yöntemi olarak HTTP veya veritabanı tüm bağımlılıklarını ekleyerek yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44d63-139">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="44d63-140">Örneğin, eShopOnContainers MVC web uygulamasından birçok hizmetlere bağlıdır, bu nedenle sistem durumu denetimlerinin eklenen birkaç AddCheck yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="44d63-140">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="44d63-141">Örneğin, aşağıdaki kodda katalog mikro hizmet bağımlılık SQL Server veritabanının nasıl ekler görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44d63-141">For instance, in the following code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

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

<span data-ttu-id="44d63-142">Ancak, eShopOnContainers MVC web uygulamasının mikro rest üzerinde birden çok bağımlılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="44d63-142">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="44d63-143">Bu nedenle, bir AddUrlCheck yöntemi her mikro hizmet için aşağıdaki örnekte gösterildiği gibi çağırır:</span><span class="sxs-lookup"><span data-stu-id="44d63-143">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following example:</span></span>

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

<span data-ttu-id="44d63-144">Bu nedenle, tüm denetimler de sağlıklı kadar bir mikro hizmet durumu "sağlıklı" sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="44d63-144">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="44d63-145">Mikro hizmet ya da SQL Server bir bağımlılık yoksa, yalnızca bir Healthy("Ok") denetimi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="44d63-145">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="44d63-146">EShopOnContainers basket.api mikro kodudur.</span><span class="sxs-lookup"><span data-stu-id="44d63-146">The following code is from the eShopOnContainers basket.api microservice.</span></span> <span data-ttu-id="44d63-147">(Redis önbelleği Sepeti mikro hizmet kullanır, ancak kitaplığı henüz bir Redis sistem durumu denetimi sağlayıcısı dahil değildir.)</span><span class="sxs-lookup"><span data-stu-id="44d63-147">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="44d63-148">UseHealthChecks etkinleştirmek olan sistem durumu denetimi uç noktayı kullanıma sunmak bir hizmeti veya web uygulaması için (\[*url\_için\_sistem durumu\_denetler*\]) uzantısı yöntem.</span><span class="sxs-lookup"><span data-stu-id="44d63-148">For a service or web application to expose the health check endpoint, it has to enable the UseHealthChecks(\[*url\_for\_health\_checks*\]) extension method.</span></span> <span data-ttu-id="44d63-149">Bu yöntem WebHostBuilder ASP.NET Core hizmeti veya web uygulamanız, sonra sağ aşağıdaki kodda gösterildiği gibi UseKestrel Program sınıfının main yöntemini düzeyde gider.</span><span class="sxs-lookup"><span data-stu-id="44d63-149">This method goes at the WebHostBuilder level in the main method of the Program class of your ASP.NET Core service or web application, right after UseKestrel as shown in the code below.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = new WebHostBuilder()
                .UseKestrel()
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseIISIntegration()
                .UseStartup<Startup>()
                .Build();
            host.Run();
        }
    }
}
```

<span data-ttu-id="44d63-150">İşlem şu şekilde çalışır: her mikro hizmet uç noktası HC kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="44d63-150">The process works like this: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="44d63-151">Bu uç HealthChecks kitaplığı ASP.NET Core ara yazılımı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="44d63-151">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="44d63-152">Bu uç çağrıldığında, başlangıç sınıfı AddHealthChecks yönteminde yapılandırılan tüm sistem durumu denetimlerini çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="44d63-152">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="44d63-153">UseHealthChecks yöntemi, bir bağlantı noktası veya bir yol bekliyor.</span><span class="sxs-lookup"><span data-stu-id="44d63-153">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="44d63-154">Bu bağlantı noktası veya yol hizmetin sistem durumunu denetlemek için uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="44d63-154">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="44d63-155">Örneğin, katalog mikro hizmet yolu HC kullanır.</span><span class="sxs-lookup"><span data-stu-id="44d63-155">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="caching-health-check-responses"></a><span data-ttu-id="44d63-156">Sistem durumu denetimi yanıt önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="44d63-156">Caching health check responses</span></span>

<span data-ttu-id="44d63-157">Çok sık hizmetlerinizi içinde bir hizmet reddi (DoS) neden istemediğiniz veya yalnızca kaynakları denetleyerek Hizmeti performansını etkileyen istemediğiniz beri döndürür önbelleğe ve her sistem durumu denetimi için bir önbellek süresi yapılandırmak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44d63-157">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="44d63-158">Varsayılan olarak, önbellek süresini dahili olarak 5 dakikaya ayarlanmıştır, ancak aşağıdaki kodu olduğu gibi her sistem durumu denetimi, önbellek süresini değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="44d63-158">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="44d63-159">Sistem durumlarına raporlamak, mikro sorgulama</span><span class="sxs-lookup"><span data-stu-id="44d63-159">Querying your microservices to report about their health status</span></span>

<span data-ttu-id="44d63-160">Mikro hizmet Docker çalışmaya başladıktan sonra burada açıklandığı gibi sistem durumu denetimlerinin yapılandırdığınızda, sağlıklı ise doğrudan bir tarayıcıdan denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44d63-160">When you have configured health checks as described here, once the microservice is running in Docker, you can directly check from a browser if it is healthy.</span></span> <span data-ttu-id="44d63-161">(Bu kapsayıcı localhost veya dış Docker ana bilgisayar IP üzerinden erişebilmesi için Docker ana kapsayıcı bağlantı noktası yayımladığınız gerektirir.) Şekil 10-7 bir isteği bir tarayıcı ve karşılık gelen yanıt gösterir.</span><span class="sxs-lookup"><span data-stu-id="44d63-161">(This does require that you are publishing the container port out of the Docker host, so you can access the container through localhost or through the external Docker host IP.) Figure 10-7 shows a request in a browser and the corresponding response.</span></span>

![](./media/image7.png)

<span data-ttu-id="44d63-162">**Şekil 10-7**.</span><span class="sxs-lookup"><span data-stu-id="44d63-162">**Figure 10-7**.</span></span> <span data-ttu-id="44d63-163">Tek bir hizmet tarayıcısından sistem durumunu denetleme</span><span class="sxs-lookup"><span data-stu-id="44d63-163">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="44d63-164">Bu test, (5101 bağlantı noktasında çalışan) catalog.api mikro hizmet sağlıklı, HTTP durum 200 ve durum bilgilerini JSON'de döndüren görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44d63-164">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="44d63-165">Ayrıca dahili olarak hizmet ayrıca SQL Server veritabanı bağımlılık durumunu işaretli olduğunu ve sistem durumu denetimi kendisini sağlıklı olarak rapor edilmiştir olduğunu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="44d63-165">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="using-watchdogs"></a><span data-ttu-id="44d63-166">Watchdogs kullanma</span><span class="sxs-lookup"><span data-stu-id="44d63-166">Using watchdogs</span></span>

<span data-ttu-id="44d63-167">Bir izleme, sistem durumu izleyebilir ve daha önce sunulan HealthChecks kitaplıkla sorgulayarak Hizmetleri ve mikro hizmetler hakkında rapor sistem genelinde yük ayrı bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="44d63-167">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the HealthChecks library introduced earlier.</span></span> <span data-ttu-id="44d63-168">Bu, tek bir hizmeti görünümü temel alarak algılanmayacağı hataları önlemeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="44d63-168">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="44d63-169">Watchdogs de iyi bir kullanıcı etkileşimi olmadan bilinen koşulları için düzeltme eylemleri gerçekleştirebilirsiniz konak koduna yerdir.</span><span class="sxs-lookup"><span data-stu-id="44d63-169">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="44d63-170">EShopOnContainers örnek örnek sistem durumu denetimi raporları, Şekil 10-8'de gösterildiği gibi görüntüleyen bir web sayfası içerir.</span><span class="sxs-lookup"><span data-stu-id="44d63-170">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 10-8.</span></span> <span data-ttu-id="44d63-171">Sahip olabilir, basit izleme budur eShopOnContainers mikro ve web uygulamalarında durumunu itibaren tüm olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="44d63-171">This is the simplest watchdog you could have, since all it does is shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="44d63-172">Genellikle sağlıksız durumları algıladığında bir izleme de eylemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="44d63-172">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![](./media/image8.png)

<span data-ttu-id="44d63-173">**Şekil 10-8**.</span><span class="sxs-lookup"><span data-stu-id="44d63-173">**Figure 10-8**.</span></span> <span data-ttu-id="44d63-174">Örnek sistem durumu denetimi eShopOnContainers raporda</span><span class="sxs-lookup"><span data-stu-id="44d63-174">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="44d63-175">Özet olarak, ASP.NET ara yazılım ASP.NET Core HealthChecks kitaplığının her mikro hizmet için bir tek sistem durumu denetimi uç noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="44d63-175">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="44d63-176">İçinde tanımlanan tüm sistem durumu denetimleri yürütmek ve genel durumu bu denetimlerini bağlı olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="44d63-176">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="44d63-177">Gelecekteki dış kaynaklara yeni durumu denetimleri Genişletilebilir HealthChecks kitaplığıdır.</span><span class="sxs-lookup"><span data-stu-id="44d63-177">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="44d63-178">Örneğin, gelecekte kitaplığı sistem durumu denetimlerinin ve diğer veritabanlarına Redis önbelleği için sahip olma olasılığı bekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="44d63-178">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="44d63-179">Birden çok hizmet veya uygulama bağımlılıkları raporlama sistem durumu kitaplığı sağlar ve ardından bu sistem durumu denetimleri üzerinde temel eylemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44d63-179">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="44d63-180">Orchestrators kullanırken durumu denetimleri</span><span class="sxs-lookup"><span data-stu-id="44d63-180">Health checks when using orchestrators</span></span>

<span data-ttu-id="44d63-181">Mikro kullanılabilirliğini izlemek için Docker Swarm, Kubernetes ve Service Fabric gibi orchestrators düzenli aralıklarla sistem durumu denetimlerini mikro test etme isteği göndererek gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="44d63-181">To monitor the availability of your microservices, orchestrators like Docker Swarm, Kubernetes, and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="44d63-182">Ne zaman bir orchestrator bir hizmet/kapsayıcısı Bu örneği yönlendirme isteklerine durdurur sağlıksız olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="44d63-182">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="44d63-183">Ayrıca genellikle, bu kapsayıcı yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44d63-183">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="44d63-184">Örneğin, çoğu orchestrators, sistem durumu denetimlerinin sıfır kapalı kalma süresi dağıtımları yönetmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44d63-184">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="44d63-185">Yalnızca hizmet/kapsayıcısı değişiklikler sağlıklı durumunu olur, orchestrator hizmet/kapsayıcısı örneklerine yönlendirme trafiğini başlatın.</span><span class="sxs-lookup"><span data-stu-id="44d63-185">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="44d63-186">Bir orchestrator uygulama yükseltme yaparken, sistem durumu izleme özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="44d63-186">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="44d63-187">Bazı orchestrators (gibi Azure Service Fabric) Hizmetleri'nde aşamaları güncelleştirme — Örneğin, her uygulama yükseltmesi için küme yüzey bir beşinci güncelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="44d63-187">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="44d63-188">Aynı anda yükseltilir düğümleri kümesi olarak adlandırılır bir *yükseltme etki alanı*.</span><span class="sxs-lookup"><span data-stu-id="44d63-188">The set of nodes that is upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="44d63-189">Her bir yükseltme etki alanı yükseltildikten ve kullanıcılar için kullanılabilir olduktan sonra dağıtım için bir sonraki yükseltme etki alanına geçmeden önce yükseltme etki alanı durumu denetimleri geçmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="44d63-189">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="44d63-190">Bir diğer unsuru hizmet sistem durumu hizmetinden ölçümleri bildiriyor.</span><span class="sxs-lookup"><span data-stu-id="44d63-190">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="44d63-191">Bu, Service Fabric gibi bazı orchestrators sistem durumu modeli, Gelişmiş bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="44d63-191">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="44d63-192">Kaynak kullanımı dengelemek için kullanıldığından bir orchestrator kullanırken ölçümleri önemlidir.</span><span class="sxs-lookup"><span data-stu-id="44d63-192">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="44d63-193">Ölçümleri de sistem durumu bir göstergesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="44d63-193">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="44d63-194">Örneğin, birçok mikro olan bir uygulama olabilir ve bir saniyedeki istek (RPS) ölçümü her örnek raporlar.</span><span class="sxs-lookup"><span data-stu-id="44d63-194">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="44d63-195">Bir hizmet başka bir hizmete daha fazla kaynak (bellek, işlemci, vb.) kullanıyorsanız, orchestrator hizmet örneklerini bile kaynak kullanımını korumak denemek için kümeye taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44d63-195">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="44d63-196">Azure Service Fabric kullanıyorsanız, bunu kendi sağladığını unutmayın [sistem durumu izleme modeli](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), basit durumu denetimleri daha gelişmiş olduğu.</span><span class="sxs-lookup"><span data-stu-id="44d63-196">Note that if you are using Azure Service Fabric, it provides its own [Health Monitoring model](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="44d63-197">İzleme Gelişmiş: Görselleştirme, analiz ve uyarılar</span><span class="sxs-lookup"><span data-stu-id="44d63-197">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="44d63-198">İzleme son bölümü hizmet performansını raporlama ve bir sorun algılandığında uyarı olay akışının görselleştirme.</span><span class="sxs-lookup"><span data-stu-id="44d63-198">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="44d63-199">Bu durum izlemenin farklı çözümler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44d63-199">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="44d63-200">Hizmetlerinizin durumunu gösteren basit özel uygulamalar kullanabilirsiniz, özel sayfa gibi biz zaman biz açıklandığı gösterdi [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="44d63-200">You can use simple custom applications showing the state of your services, like the custom page we showed when we explained [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span></span> <span data-ttu-id="44d63-201">Veya Azure Application Insights ve Operations Management Suite gibi daha gelişmiş araçlar olayları akışa göre uyarıları yükseltmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44d63-201">Or you could use more advanced tools like Azure Application Insights and Operations Management Suite to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="44d63-202">Tüm olay akışları depolanıyorsa son olarak, Microsoft Power BI veya bir üçüncü taraf çözümü Kibana veya Splunk gibi verileri görselleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44d63-202">Finally, if you were storing all the event streams, you can use Microsoft Power BI or a third-party solution like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="44d63-203">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="44d63-203">Additional resources</span></span>

-   <span data-ttu-id="44d63-204">**ASP.NET Core HealthChecks** (ilk sürüm) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span><span class="sxs-lookup"><span data-stu-id="44d63-204">**ASP.NET Core HealthChecks** (early release) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span></span>

-   <span data-ttu-id="44d63-205">**Service Fabric sistem durumu izlemeye giriş**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="44d63-205">**Introduction to Service Fabric health monitoring**
[*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="44d63-206">**Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="44d63-206">**Azure Application Insights**
[*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="44d63-207">**Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="44d63-207">**Microsoft Operations Management Suite**
[*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="44d63-208">[Önceki](implement-circuit-breaker-pattern.md)
[sonraki](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="44d63-208">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>
