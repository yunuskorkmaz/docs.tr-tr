---
title: Sistem durumu izleme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Sistem durumu izleme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 35f6d773d714878f56a5e9151320072ebcd51e06
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145981"
---
# <a name="health-monitoring"></a><span data-ttu-id="ba6c4-103">Sistem durumu izleme</span><span class="sxs-lookup"><span data-stu-id="ba6c4-103">Health monitoring</span></span>

<span data-ttu-id="ba6c4-104">Sistem durumu izleme, kapsayıcılar ve mikro hizmet durumu hakkında neredeyse gerçek zamanlı bilgi izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="ba6c4-105">Sistem durumu izleme, kritik işletme mikro hizmetler birçok yönünü ve düzenleyicileri kısmi uygulama yükseltmeleri aşamalarında, daha sonra açıklandığı gibi gerçekleştirin, özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="ba6c4-106">Mikro hizmet tabanlı uygulamalar genellikle sinyal kullanabilir veya kendi performans izleyicileri, zamanlayıcılar ve düzenleyicileri birçok izlemenize olanak sağlamak için sistem durumu denetimleri.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="ba6c4-107">Hizmetleri "I canlı" bir sinyal çeşit isteğe bağlı veya bir zamanlamaya göre gönderemiyorsanız riskleri uygulamanızı yüz güncelleştirmelerini dağıtma veya yalnızca çok geç hatalarını algılamak ve ana kesintilerine sona erdirebilirsiniz zincirleme hatalara durdurmak mümkün olmaması.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might simply detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="ba6c4-108">Tipik modelinde Hizmetleri durumlarını hakkında raporlar gönderin ve uygulama durumunu durumunun genel bir görünümünü sağlamak için bu bilgileri toplanır.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="ba6c4-109">Bir orchestrator kullanıyorsanız, küme uygun şekilde işlem yapabilmesi, düzenleyicinin küme sistem durumu bilgilerini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-109">If you are using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="ba6c4-110">Uygulamanız için özelleştirilmiş, yüksek kaliteli sistem durumu raporlama yatırım yaparsanız, algılayın ve çalışan uygulamanız için çok daha kolay sorunları giderin.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-110">If you invest in high-quality health reporting that is customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implementing-health-checks-in-aspnet-core-services"></a><span data-ttu-id="ba6c4-111">ASP.NET Core Hizmetleri sistem durumu uygulama denetler</span><span class="sxs-lookup"><span data-stu-id="ba6c4-111">Implementing health checks in ASP.NET Core services</span></span>

<span data-ttu-id="ba6c4-112">Bir ASP.NET Core mikro hizmet veya web uygulama geliştirirken, bir bant dışı kitaplığı kullanabilirsiniz (değil resmi ASP.NETCore bir parçası olarak) adlı `HealthChecks` ASP.NET ekibinden.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-112">When developing an ASP.NET Core microservice or web application, you can use an out-of-band library (not official as part of ASP.NETCore) named `HealthChecks` from the ASP.NET team.</span></span> <span data-ttu-id="ba6c4-113">Şu anda kullanılabilir [GitHub deposunu](https://github.com/dotnet-architecture/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="ba6c4-113">It is available at this [GitHub repo](https://github.com/dotnet-architecture/HealthChecks).</span></span>

<span data-ttu-id="ba6c4-114">Bu kitaplık kullanımı kolaydır ve uygulamanız (örneğin, bir SQL Server veritabanı veya Uzak API) için gereken tüm belirli dış kaynak düzgün şekilde çalıştığını doğrulama olanak sağlayan özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-114">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="ba6c4-115">Bu kitaplığı kullandığınızda, daha sonra anlatıldığı şekilde resource sağlam, anlamı da karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-115">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="ba6c4-116">Bu kitaplığı kullanmak için öncelikle mikro hizmetlerin kitaplıkta kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-116">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="ba6c4-117">İkinci olarak, sorgular bir ön uç uygulaması için sistem durumu raporlarının gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="ba6c4-118">Ön uç uygulaması, bir özel raporlama uygulaması olabilir ya da uygun şekilde tepki verebilir bir orchestrator kendisini olabileceği için sağlık durumlarını.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-118">That front end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="ba6c4-119">Arka ucunuza ASP.NET mikro hizmetler HealthChecks kitaplıkta kullanma</span><span class="sxs-lookup"><span data-stu-id="ba6c4-119">Using the HealthChecks library in your back end ASP.NET microservices</span></span>

<span data-ttu-id="ba6c4-120">HealthChecks kitaplığı hizmetine örnek uygulamada nasıl kullanıldığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-120">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="ba6c4-121">Başlamak için her bir mikro hizmet durumu sağlıklı nelerden tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-121">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="ba6c4-122">Örnek uygulamada, mikro hizmetler, HTTP ve ilgili SQL Server veritabanını da kullanılabilir olup olmadığını API mikro hizmet erişilemez iyi durumda.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-122">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="ba6c4-123">Gelecekte bir NuGet paketi olarak HealthChecks kitaplığını yüklemek mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-123">In the future, you will be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="ba6c4-124">Ancak bu makalenin yazıldığı tarih itibarıyla, indirmek ve çözümünüzün bir parçası olarak Kodu derlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-124">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="ba6c4-125">Kullanılabilir kod klonlama https://github.com/dotnet-architecture/HealthChecks ve çözümünüze aşağıdaki klasörleri kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="ba6c4-125">Clone the code available at https://github.com/dotnet-architecture/HealthChecks and copy the following folders to your solution:</span></span>

  - <span data-ttu-id="ba6c4-126">src/ortak</span><span class="sxs-lookup"><span data-stu-id="ba6c4-126">src/common</span></span>
  - <span data-ttu-id="ba6c4-127">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="ba6c4-127">src/Microsoft.AspNetCore.HealthChecks</span></span>
  - <span data-ttu-id="ba6c4-128">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="ba6c4-128">src/Microsoft.Extensions.HealthChecks</span></span>
  - <span data-ttu-id="ba6c4-129">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="ba6c4-129">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="ba6c4-130">Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ancak bu sürümü hizmetine Azure'da herhangi bir bağımlılığı olmadığından olanlar gibi ek denetimler de kullanabilirsiniz, bunun gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-130">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="ba6c4-131">ASP.NET Core, hizmetine dayandığından, ASP.NET sistem durumu denetimleri ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-131">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="ba6c4-132">Şekil 10-6 HealthChecks Kitaplığı Visual Studio, bir yapı taşı olarak herhangi bir mikro hizmetler tarafından kullanılmaya hazır gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-132">Figure 10-6 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![](./media/image6.png)

<span data-ttu-id="ba6c4-133">**Şekil 10-6**.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-133">**Figure 10-6**.</span></span> <span data-ttu-id="ba6c4-134">ASP.NET Core HealthChecks kitaplığı kaynak kodunu bir Visual Studio çözümü içinde</span><span class="sxs-lookup"><span data-stu-id="ba6c4-134">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="ba6c4-135">Daha önce sunulan gibi her bir mikro hizmet projesine yapılacak ilk şey bir başvuru üç HealthChecks kitaplıkları eklemektir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-135">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="ba6c4-136">Bundan sonra bu mikro hizmet içinde gerçekleştirmek istediğiniz sistem durumu denetimi eylemlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-136">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="ba6c4-137">Bu eylemler temel olarak diğer mikro hizmetler (HttpUrlCheck) veya veritabanlarını bağımlılıkları olan (şu anda SqlCheck\* SQL Server veritabanları için).</span><span class="sxs-lookup"><span data-stu-id="ba6c4-137">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="ba6c4-138">Eylem içinde her ASP.NET mikro hizmet veya ASP.NET web uygulaması başlangıç sınıfı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-138">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="ba6c4-139">Her hizmeti veya web uygulamasına bir AddHealthCheck yöntemi olarak HTTP ya da veritabanı tüm bağımlılıkları ekleyerek yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-139">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="ba6c4-140">Örneğin, MVC web hizmetine uygulamadan birden çok hizmete bağlıdır, bu nedenle, sistem durumu denetimleri için eklenen çeşitli AddCheck yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-140">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="ba6c4-141">Örneğin, aşağıdaki kodda nasıl Kataloğu mikro hizmet kendi SQL Server veritabanı üzerinde bir bağımlılık ekler görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-141">For instance, in the following code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

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

<span data-ttu-id="ba6c4-142">Ancak, hizmetine MVC web uygulaması, mikro hizmetler geri kalanı üzerinde birden çok bağımlılıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-142">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="ba6c4-143">Bu nedenle, bir AddUrlCheck yöntemini her mikro hizmet için aşağıdaki örnekte gösterildiği gibi çağırır:</span><span class="sxs-lookup"><span data-stu-id="ba6c4-143">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following example:</span></span>

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

<span data-ttu-id="ba6c4-144">Bu nedenle, tüm denetimleri de sağlıklı olduğunu kadar bir mikro hizmet "iyi" duruma sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-144">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="ba6c4-145">Mikro hizmet veya SQL Server bir bağımlılık yoksa, yalnızca bir Healthy("Ok") onay eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-145">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="ba6c4-146">Hizmetine basket.api mikro hizmet kodudur.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-146">The following code is from the eShopOnContainers basket.api microservice.</span></span> <span data-ttu-id="ba6c4-147">(Redis cache sepet mikro hizmet kullanır, ancak kitaplık bir Redis sistem durumu denetimi sağlayıcısı henüz içermez.)</span><span class="sxs-lookup"><span data-stu-id="ba6c4-147">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="ba6c4-148">UseHealthChecks etkinleştirmek olan sistem durumu onay uç noktası kullanıma sunmak bir hizmeti veya web uygulaması için (\[*url\_için\_sistem durumu\_denetler*\]) uzantısı yöntem.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-148">For a service or web application to expose the health check endpoint, it has to enable the UseHealthChecks(\[*url\_for\_health\_checks*\]) extension method.</span></span> <span data-ttu-id="ba6c4-149">Bu yöntem WebHostBuilder ana yöntemde, ASP.NET Core hizmeti veya web uygulaması, aşağıdaki kodda gösterildiği gibi sağ UseKestrel sonra Program sınıfının düzeyi gider.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-149">This method goes at the WebHostBuilder level in the main method of the Program class of your ASP.NET Core service or web application, right after UseKestrel as shown in the code below.</span></span>

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

<span data-ttu-id="ba6c4-150">İşlem şu şekilde çalışır: her mikro hizmet uç noktası HC kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-150">The process works like this: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="ba6c4-151">Uç noktanın HealthChecks kitaplığı ASP.NET Core ara yazılımı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-151">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="ba6c4-152">Uç noktanın çağrıldığında başlangıç sınıfındaki AddHealthChecks yöntemi yapılandırılan tüm sistem durumu denetimleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-152">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="ba6c4-153">Bir bağlantı noktası veya yol UseHealthChecks yöntemi bekliyor.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-153">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="ba6c4-154">Bu bağlantı noktası veya yol, hizmetin sistem durumunu denetlemek için uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-154">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="ba6c4-155">Örneğin, katalog mikro hizmet yolu HC kullanır.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-155">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="caching-health-check-responses"></a><span data-ttu-id="ba6c4-156">Sistem durumu onay yanıtları önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="ba6c4-156">Caching health check responses</span></span>

<span data-ttu-id="ba6c4-157">Çok sık hizmetlerinizde bir hizmet reddi (DoS) neden istemediğiniz veya yalnızca kaynak kontrol ederek hizmet performansı etkileyecek şekilde istemiyorsanız bu yana önbelleğe döndürür ve önbelleğe alma süresi her sistem durumu denetimi için yapılandırma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-157">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="ba6c4-158">Varsayılan olarak, önbelleğe alma süresi 5 dakika ile dahili olarak ayarlanır, ancak bu önbelleğe alma süresi şu kod gibi her sistem durumu denetimi üzerinde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ba6c4-158">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="ba6c4-159">Mikro hizmetlerin sistem durumlarına raporlamak sorgulama</span><span class="sxs-lookup"><span data-stu-id="ba6c4-159">Querying your microservices to report about their health status</span></span>

<span data-ttu-id="ba6c4-160">Sistem durumu denetimleri, bir Docker mikro hizmet çalışmaya başladıktan sonra burada açıklanan şekilde yapılandırdığınızda, sağlıksız olması durumunda doğrudan bir tarayıcıdan denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-160">When you have configured health checks as described here, once the microservice is running in Docker, you can directly check from a browser if it is healthy.</span></span> <span data-ttu-id="ba6c4-161">(Bu kapsayıcı veya dış Docker ana bilgisayar IP'SİNİN localhost aracılığıyla erişebilmesi için Docker konağı kapsayıcı bağlantı noktası yayımladığınız gerektirir.) Şekil 10-7, bir tarayıcı ve karşılık gelen yanıt bir istek gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-161">(This does require that you are publishing the container port out of the Docker host, so you can access the container through localhost or through the external Docker host IP.) Figure 10-7 shows a request in a browser and the corresponding response.</span></span>

![](./media/image7.png)

<span data-ttu-id="ba6c4-162">**Şekil 10-7**.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-162">**Figure 10-7**.</span></span> <span data-ttu-id="ba6c4-163">Tek bir hizmet tarayıcısından sistem durumunu denetleme</span><span class="sxs-lookup"><span data-stu-id="ba6c4-163">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="ba6c4-164">Bu test, (5101 bağlantı noktasında çalışan) catalog.api mikro hizmet sağlıklı, 200 HTTP durum ve durum bilgileri JSON biçiminde döndüren görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-164">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="ba6c4-165">Ayrıca dahili olarak hizmet aynı zamanda SQL Server veritabanı bağımlılık durumunu iade etmeniz ve sistem durumu denetimi kendisini sağlıklı olarak rapor edilmiştir, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-165">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="using-watchdogs"></a><span data-ttu-id="ba6c4-166">Watchdogs kullanma</span><span class="sxs-lookup"><span data-stu-id="ba6c4-166">Using watchdogs</span></span>

<span data-ttu-id="ba6c4-167">Bir izleme sistem durumu izleyin ve daha önce sunulan HealthChecks kitaplığıyla sorgulayarak Hizmetleri ve mikro hizmetler hakkında rapor sistem genelinde yük ayrı bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-167">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the HealthChecks library introduced earlier.</span></span> <span data-ttu-id="ba6c4-168">Bu işlem, tek bir hizmette bir görünümü temel alarak değil algılanır hataları önlemeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-168">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="ba6c4-169">Watchdogs de iyi bir kullanıcı etkileşimi olmadan bilinen koşulları için düzeltme eylemleri gerçekleştirebilen konak koda yerdir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-169">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="ba6c4-170">Şekil 10-8'de gösterildiği örnek sistem durumu denetimi raporları görüntüleyen bir web sayfası hizmetine örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-170">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 10-8.</span></span> <span data-ttu-id="ba6c4-171">Bu, sahip olabilir, en basit izleme, mikro hizmetler ve web uygulamalarını hizmetine durumunu itibaren tüm olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-171">This is the simplest watchdog you could have, since all it does is shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="ba6c4-172">Genellikle, iyi durumda olmayan durumlar algıladığında bir bekçi ayrıca eylemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-172">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![](./media/image8.png)

<span data-ttu-id="ba6c4-173">**Şekil 10-8**.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-173">**Figure 10-8**.</span></span> <span data-ttu-id="ba6c4-174">Hizmetine örnek sistem durumu denetimi raporu</span><span class="sxs-lookup"><span data-stu-id="ba6c4-174">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="ba6c4-175">Özet olarak, ASP.NET, ASP.NET Core HealthChecks kitaplığının tek sistem durumu onay uç noktası için her bir mikro hizmetin ihtiyacımızı karşılıyor.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-175">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="ba6c4-176">İçinde tanımlanan tüm sistem durumu denetimleri yürütmek ve genel sistem durumuna bağlı tüm denetimleri olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-176">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="ba6c4-177">Gelecekteki dış kaynaklara yeni sistem durumu denetimleri Genişletilebilir HealthChecks kitaplığıdır.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-177">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="ba6c4-178">Örneğin, gelecekte kitaplığı diğer veritabanları ve Redis önbelleği için sistem durumu denetimleri olacağını umuyoruz.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-178">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="ba6c4-179">Birden çok hizmet veya uygulama bağımlılıkları raporlama sistem durumu kitaplığı sağlar ve sonra bu sistem durumu denetimleri üzerinde temel eylemleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-179">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="ba6c4-180">Düzenleyiciler kullanırken sistem durumu denetimleri</span><span class="sxs-lookup"><span data-stu-id="ba6c4-180">Health checks when using orchestrators</span></span>

<span data-ttu-id="ba6c4-181">Mikro hizmetlerin kullanılabilirliğini izlemek için Docker Swarm, Kubernetes ve Service Fabric gibi düzenleyicilerle düzenli aralıklarla sistem durumu denetimleri mikro Hizmetleri test etmek için istekleri göndererek gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-181">To monitor the availability of your microservices, orchestrators like Docker Swarm, Kubernetes, and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="ba6c4-182">Ne zaman bir orchestrator hizmet/kapsayıcı yönlendirme istekleri bu örneği durdurur, sağlıksız olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-182">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="ba6c4-183">Ayrıca genellikle, bu kapsayıcı yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-183">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="ba6c4-184">Örneğin, çoğu düzenleyicileri, sistem durumu denetimleri kesintisiz dağıtımlarını yönetmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-184">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="ba6c4-185">Yalnızca sağlıklı bir hizmeti/kapsayıcı değişiklikleri durumunu olacak orchestrator başlattığınızda hizmet/kapsayıcı örneklerine trafiği yönlendirme.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-185">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="ba6c4-186">Bir orchestrator uygulama yükseltme yaparken, sistem durumu izleme özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-186">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="ba6c4-187">Bazı düzenleyiciler (örneğin, Azure Service Fabric) Hizmetleri'nde aşamaları güncelleştirme — Örneğin, her uygulama yükseltmesi için küme yüzeyinde bir beşinci güncelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-187">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="ba6c4-188">Aynı anda yükseltilir düğümleri kümesini şeklinde adlandırılan bir *yükseltme etki alanı*.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-188">The set of nodes that is upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="ba6c4-189">Her bir yükseltme etki alanı yükseltildi ve kullanıcılar tarafından kullanılabilir sonra dağıtım için bir sonraki yükseltme etki alanına taşınmadan önce yükseltme etki alanı sistem durumu denetimleri geçmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-189">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="ba6c4-190">Bir diğer unsuru hizmet sistem durumu hizmetinden alınan ölçümleri bildiriyor.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-190">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="ba6c4-191">Bu, Service Fabric gibi bazı düzenleyiciler sistem durumu modeli, Gelişmiş bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-191">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="ba6c4-192">Ölçümler, kaynak kullanımı dengelemek için kullanıldığından bir orchestrator kullanırken önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-192">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="ba6c4-193">Ölçümleri de sistem durumu göstergesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-193">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="ba6c4-194">Örneğin, birçok mikro olan bir uygulama olabilir ve her örneği bir saniyede istekleri (RP'ler) ölçüm bildirir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-194">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="ba6c4-195">Bir hizmetin başka bir hizmete daha fazla kaynak (bellek, işlemci, vb.) kullanıyorsanız, orchestrator hizmet örnekleri bile kaynak kullanımını korumak için kümedeki yerleri.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-195">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="ba6c4-196">Azure Service Fabric kullanıyorsanız, bunu kendi sağladığını unutmayın [sistem durumu izleme modeli](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), basit bir sistem durumu denetimleri daha gelişmiş olduğu.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-196">Note that if you are using Azure Service Fabric, it provides its own [Health Monitoring model](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="ba6c4-197">Gelişmiş izleme: Görselleştirme ve çözümleme uyarıları</span><span class="sxs-lookup"><span data-stu-id="ba6c4-197">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="ba6c4-198">İzleme son bölümü göre servis performansını raporlama ve bir sorun algılandığında uyarı olay akışını görselleştirme olduğu.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-198">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="ba6c4-199">Bu izleme açısını için farklı çözümler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-199">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="ba6c4-200">Hizmetlerinizin durumunu gösteren basit bir özel uygulamalar kullanabilir, özel sayfa gibi biz size zaman açıklandığı gösterdi. [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="ba6c4-200">You can use simple custom applications showing the state of your services, like the custom page we showed when we explained [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span></span> <span data-ttu-id="ba6c4-201">Veya Azure Application Insights ve Operations Management Suite gibi daha gelişmiş araçlar, olayların akışa göre uyarıları yükseltmek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-201">Or you could use more advanced tools like Azure Application Insights and Operations Management Suite to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="ba6c4-202">Depoladığınız tüm olay akışları, son olarak, Microsoft Power BI veya Kibana veya Splunk gibi bir üçüncü taraf çözümünü verileri görselleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba6c4-202">Finally, if you were storing all the event streams, you can use Microsoft Power BI or a third-party solution like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ba6c4-203">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="ba6c4-203">Additional resources</span></span>

-   <span data-ttu-id="ba6c4-204">**ASP.NET Core HealthChecks** (önceki sürüm) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span><span class="sxs-lookup"><span data-stu-id="ba6c4-204">**ASP.NET Core HealthChecks** (early release) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span></span>

-   <span data-ttu-id="ba6c4-205">**Service Fabric sistem durumu izlemeye giriş**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="ba6c4-205">**Introduction to Service Fabric health monitoring**
[*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="ba6c4-206">**Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="ba6c4-206">**Azure Application Insights**
[*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="ba6c4-207">**Microsoft Operations Management Suite'e**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="ba6c4-207">**Microsoft Operations Management Suite**
[*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ba6c4-208">[Önceki](implement-circuit-breaker-pattern.md)
>[İleri](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="ba6c4-208">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>