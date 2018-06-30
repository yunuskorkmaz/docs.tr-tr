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
# <a name="health-monitoring"></a>Sistem durumu izleme

Sistem durumu izleme durumunu kapsayıcıları ve mikro hizmetler hakkında bilgi yakın gerçek zamanlı izin verebilirsiniz. Sistem durumu izleme mikro işletim birden çok yönlerini için kritik öneme sahiptir ve orchestrators kısmi uygulama yükseltmelerini aşamalarında, daha sonra açıklandığı gibi gerçekleştirdiğinizde özellikle önemlidir.

Mikro tabanlı uygulamalar genellikle sinyal kullanabilir veya kendi performans izleyicileri, zamanlayıcılar ve orchestrators birçok izlemenize olanak sağlamak için sistem durumu denetler. Hizmetleri "Canlı ben" sinyal çeşit isteğe bağlı veya bir zamanlamaya göre gönderemiyor, uygulamanız güncelleştirmeleri dağıtırken veya yalnızca hatalarını çok geç algılayacak ve önemli kesilmelerini sonlandırabilirsiniz basamaklı hataları Durdur yükleyemeyebilirsiniz riskleri karşılaşıyor.

Tipik modelinde Hizmetleri durumları hakkında rapor gönderme ve sistem durumu, uygulamanızın durumunu genel bir görünümünü sağlamak için bu bilgileri toplanır. Bir orchestrator kullanıyorsanız, böylece küme buna uygun olarak davranıp orchestrator'ın küme, sistem durumu bilgilerini sağlayabilir. Yüksek kaliteli sistem durumu, uygulamanız için özelleştirilmiş raporlamada yatırım algılamak ve çalışan uygulamanız için daha kolay düzeltin.

## <a name="implementing-health-checks-in-aspnet-core-services"></a>Sistem durumu uygulama ASP.NET Core Hizmetleri'nde denetler

Bir ASP.NET Core mikro hizmet veya web uygulama geliştirirken, bir bant dışı kitaplığını kullanabilirsiniz (değil resmi ASP.NETCore bir parçası olarak) adlı `HealthChecks` ASP.NET ekibinden. Şu anda kullanılabilir [GitHub deposuna](https://github.com/dotnet-architecture/HealthChecks).

Bu kitaplık kullanımı kolaydır ve uygulamanız (örneğin, bir SQL Server veritabanı veya Uzak API) için gerekli herhangi belirli bir dış kaynağa düzgün çalıştığını doğrulamak olanak sağlayan özellikleri sağlar. Bu kitaplık kullandığınızda, daha sonra anlatıldığı şekilde kaynağın sistem durumunun iyi olduğundan anlamını da karar verebilirsiniz.

Bu kitaplığı kullanmak için önce mikro kitaplıkta kullanmanız gerekebilir. İkinci olarak, sistem durumu raporları sorgular bir ön uç uygulaması gerekir. Ön uç uygulama, özel bir raporlama uygulama olabilir ya da, uygun şekilde tepki gösterebilmesi bir orchestrator kendisini olabilir sistem sağlığı durumları.

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>Arka ucunuz ASP.NET mikro HealthChecks kitaplıkta kullanma

HealthChecks kitaplığı eShopOnContainers örnek uygulama nasıl kullanıldığını görebilirsiniz. Başlamak için her mikro hizmet durumu sağlıklı nelerin oluşturduğunu tanımlamanız gerekir. Örnek uygulama mikro API mikro HTTP ve ilgili SQL Server veritabanını da kullanılabilir olup olmadığını aracılığıyla erişilebilir olması durumunda iyi durumda.

Gelecekte, bir NuGet paketi olarak HealthChecks Kitaplığı'nı yüklemek mümkün olacaktır. Ancak bu makalenin yazıldığı sırada indirmek ve çözümünüzün bir parçası olarak Kodu derlemek gerekir. Adresinde kod kopyalama https://github.com/dotnet-architecture/HealthChecks ve aşağıdaki klasörler çözümünüze kopyalayın:

  - src/ortak
  - src/Microsoft.AspNetCore.HealthChecks
  - src/Microsoft.Extensions.HealthChecks
  - src/Microsoft.Extensions.HealthChecks.SqlServer

Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ancak bu sürümü eShopOnContainers, Azure üzerinde herhangi bir bağımlılığı olmadığından olanlar gibi ek denetimler de kullanabilirsiniz, onu gerekmez. EShopOnContainers ASP.NET Core üzerinde bağlı olduğundan, ASP.NET durumu denetimleri gerekmez.

Şekil 10-6 HealthChecks Kitaplığı Visual Studio, bir yapı taşı olarak tüm mikro tarafından kullanılmak üzere hazır gösterir.

![](./media/image6.png)

**Şekil 10-6**. ASP.NET Core HealthChecks kitaplığı kaynak kodundaki bir Visual Studio çözümü

Daha önce sunulan gibi her mikro hizmet projesinde yapılacak ilk şey üç HealthChecks kitaplıklar için bir başvuru eklemeniz gereklidir. Bundan sonra o mikro gerçekleştirmek istediğiniz sistem durumu denetimi eylemlerini ekleyin. Bu eylemler temelde diğer mikro (HttpUrlCheck) veya veritabanlarını bağımlılıklardır (şu anda SqlCheck\* SQL Server veritabanları için). Eylem içinde her ASP.NET mikro hizmet veya ASP.NET web uygulaması başlangıç sınıfı ekleyin.

Her hizmeti veya web uygulamasını bir AddHealthCheck yöntemi olarak HTTP veya veritabanı tüm bağımlılıklarını ekleyerek yapılandırılması gerekir. Örneğin, eShopOnContainers MVC web uygulamasından birçok hizmetlere bağlıdır, bu nedenle sistem durumu denetimlerinin eklenen birkaç AddCheck yöntemlerine sahiptir.

Örneğin, aşağıdaki kodda katalog mikro hizmet bağımlılık SQL Server veritabanının nasıl ekler görebilirsiniz.

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

Ancak, eShopOnContainers MVC web uygulamasının mikro rest üzerinde birden çok bağımlılıkları vardır. Bu nedenle, bir AddUrlCheck yöntemi her mikro hizmet için aşağıdaki örnekte gösterildiği gibi çağırır:

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

Bu nedenle, tüm denetimler de sağlıklı kadar bir mikro hizmet durumu "sağlıklı" sağlamaz.

Mikro hizmet ya da SQL Server bir bağımlılık yoksa, yalnızca bir Healthy("Ok") denetimi eklemeniz gerekir. EShopOnContainers basket.api mikro kodudur. (Redis önbelleği Sepeti mikro hizmet kullanır, ancak kitaplığı henüz bir Redis sistem durumu denetimi sağlayıcısı dahil değildir.)

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

UseHealthChecks etkinleştirmek olan sistem durumu denetimi uç noktayı kullanıma sunmak bir hizmeti veya web uygulaması için (\[*url\_için\_sistem durumu\_denetler*\]) uzantısı yöntem. Bu yöntem WebHostBuilder ASP.NET Core hizmeti veya web uygulamanız, sonra sağ aşağıdaki kodda gösterildiği gibi UseKestrel Program sınıfının main yöntemini düzeyde gider.

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

İşlem şu şekilde çalışır: her mikro hizmet uç noktası HC kullanıma sunar. Bu uç HealthChecks kitaplığı ASP.NET Core ara yazılımı tarafından oluşturulur. Bu uç çağrıldığında, başlangıç sınıfı AddHealthChecks yönteminde yapılandırılan tüm sistem durumu denetimlerini çalıştırır.

UseHealthChecks yöntemi, bir bağlantı noktası veya bir yol bekliyor. Bu bağlantı noktası veya yol hizmetin sistem durumunu denetlemek için uç noktadır. Örneğin, katalog mikro hizmet yolu HC kullanır.

### <a name="caching-health-check-responses"></a>Sistem durumu denetimi yanıt önbelleğe alma

Çok sık hizmetlerinizi içinde bir hizmet reddi (DoS) neden istemediğiniz veya yalnızca kaynakları denetleyerek Hizmeti performansını etkileyen istemediğiniz beri döndürür önbelleğe ve her sistem durumu denetimi için bir önbellek süresi yapılandırmak kullanabilirsiniz.

Varsayılan olarak, önbellek süresini dahili olarak 5 dakikaya ayarlanmıştır, ancak aşağıdaki kodu olduğu gibi her sistem durumu denetimi, önbellek süresini değiştirebilirsiniz:

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a>Sistem durumlarına raporlamak, mikro sorgulama

Mikro hizmet Docker çalışmaya başladıktan sonra burada açıklandığı gibi sistem durumu denetimlerinin yapılandırdığınızda, sağlıklı ise doğrudan bir tarayıcıdan denetleyebilirsiniz. (Bu kapsayıcı localhost veya dış Docker ana bilgisayar IP üzerinden erişebilmesi için Docker ana kapsayıcı bağlantı noktası yayımladığınız gerektirir.) Şekil 10-7 bir isteği bir tarayıcı ve karşılık gelen yanıt gösterir.

![](./media/image7.png)

**Şekil 10-7**. Tek bir hizmet tarayıcısından sistem durumunu denetleme

Bu test, (5101 bağlantı noktasında çalışan) catalog.api mikro hizmet sağlıklı, HTTP durum 200 ve durum bilgilerini JSON'de döndüren görebilirsiniz. Ayrıca dahili olarak hizmet ayrıca SQL Server veritabanı bağımlılık durumunu işaretli olduğunu ve sistem durumu denetimi kendisini sağlıklı olarak rapor edilmiştir olduğunu anlamına gelir.

## <a name="using-watchdogs"></a>Watchdogs kullanma

Bir izleme, sistem durumu izleyebilir ve daha önce sunulan HealthChecks kitaplıkla sorgulayarak Hizmetleri ve mikro hizmetler hakkında rapor sistem genelinde yük ayrı bir hizmettir. Bu, tek bir hizmeti görünümü temel alarak algılanmayacağı hataları önlemeye yardımcı olabilir. Watchdogs de iyi bir kullanıcı etkileşimi olmadan bilinen koşulları için düzeltme eylemleri gerçekleştirebilirsiniz konak koduna yerdir.

EShopOnContainers örnek örnek sistem durumu denetimi raporları, Şekil 10-8'de gösterildiği gibi görüntüleyen bir web sayfası içerir. Sahip olabilir, basit izleme budur eShopOnContainers mikro ve web uygulamalarında durumunu itibaren tüm olduğunu gösterir. Genellikle sağlıksız durumları algıladığında bir izleme de eylemleri gerçekleştirir.

![](./media/image8.png)

**Şekil 10-8**. Örnek sistem durumu denetimi eShopOnContainers raporda

Özet olarak, ASP.NET ara yazılım ASP.NET Core HealthChecks kitaplığının her mikro hizmet için bir tek sistem durumu denetimi uç noktası sağlar. İçinde tanımlanan tüm sistem durumu denetimleri yürütmek ve genel durumu bu denetimlerini bağlı olarak döndürür.

Gelecekteki dış kaynaklara yeni durumu denetimleri Genişletilebilir HealthChecks kitaplığıdır. Örneğin, gelecekte kitaplığı sistem durumu denetimlerinin ve diğer veritabanlarına Redis önbelleği için sahip olma olasılığı bekliyoruz. Birden çok hizmet veya uygulama bağımlılıkları raporlama sistem durumu kitaplığı sağlar ve ardından bu sistem durumu denetimleri üzerinde temel eylemleri gerçekleştirebilirsiniz.

## <a name="health-checks-when-using-orchestrators"></a>Orchestrators kullanırken durumu denetimleri

Mikro kullanılabilirliğini izlemek için Docker Swarm, Kubernetes ve Service Fabric gibi orchestrators düzenli aralıklarla sistem durumu denetimlerini mikro test etme isteği göndererek gerçekleştirin. Ne zaman bir orchestrator bir hizmet/kapsayıcısı Bu örneği yönlendirme isteklerine durdurur sağlıksız olduğunu belirler. Ayrıca genellikle, bu kapsayıcı yeni bir örneğini oluşturur.

Örneğin, çoğu orchestrators, sistem durumu denetimlerinin sıfır kapalı kalma süresi dağıtımları yönetmek için kullanabilirsiniz. Yalnızca hizmet/kapsayıcısı değişiklikler sağlıklı durumunu olur, orchestrator hizmet/kapsayıcısı örneklerine yönlendirme trafiğini başlatın.

Bir orchestrator uygulama yükseltme yaparken, sistem durumu izleme özellikle önemlidir. Bazı orchestrators (gibi Azure Service Fabric) Hizmetleri'nde aşamaları güncelleştirme — Örneğin, her uygulama yükseltmesi için küme yüzey bir beşinci güncelleştirebilir. Aynı anda yükseltilir düğümleri kümesi olarak adlandırılır bir *yükseltme etki alanı*. Her bir yükseltme etki alanı yükseltildikten ve kullanıcılar için kullanılabilir olduktan sonra dağıtım için bir sonraki yükseltme etki alanına geçmeden önce yükseltme etki alanı durumu denetimleri geçmesi gerekir.

Bir diğer unsuru hizmet sistem durumu hizmetinden ölçümleri bildiriyor. Bu, Service Fabric gibi bazı orchestrators sistem durumu modeli, Gelişmiş bir özelliktir. Kaynak kullanımı dengelemek için kullanıldığından bir orchestrator kullanırken ölçümleri önemlidir. Ölçümleri de sistem durumu bir göstergesi olabilir. Örneğin, birçok mikro olan bir uygulama olabilir ve bir saniyedeki istek (RPS) ölçümü her örnek raporlar. Bir hizmet başka bir hizmete daha fazla kaynak (bellek, işlemci, vb.) kullanıyorsanız, orchestrator hizmet örneklerini bile kaynak kullanımını korumak denemek için kümeye taşıyabilirsiniz.

Azure Service Fabric kullanıyorsanız, bunu kendi sağladığını unutmayın [sistem durumu izleme modeli](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), basit durumu denetimleri daha gelişmiş olduğu.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>İzleme Gelişmiş: Görselleştirme, analiz ve uyarılar

İzleme son bölümü hizmet performansını raporlama ve bir sorun algılandığında uyarı olay akışının görselleştirme. Bu durum izlemenin farklı çözümler kullanabilirsiniz.

Hizmetlerinizin durumunu gösteren basit özel uygulamalar kullanabilirsiniz, özel sayfa gibi biz zaman biz açıklandığı gösterdi [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks). Veya Azure Application Insights ve Operations Management Suite gibi daha gelişmiş araçlar olayları akışa göre uyarıları yükseltmek için kullanabilirsiniz.

Tüm olay akışları depolanıyorsa son olarak, Microsoft Power BI veya bir üçüncü taraf çözümü Kibana veya Splunk gibi verileri görselleştirmek için kullanabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

-   **ASP.NET Core HealthChecks** (ilk sürüm) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)

-   **Service Fabric sistem durumu izlemeye giriş**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)

-   **Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

-   **Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
[Önceki](implement-circuit-breaker-pattern.md)
[sonraki](../secure-net-microservices-web-applications/index.md)
